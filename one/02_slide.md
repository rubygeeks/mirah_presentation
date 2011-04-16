!SLIDE bullets incremental
# What Ruby currently Lacks #
* need for a production web server apache/nginx
* bigger memory footprint/GC issues
* bridges are not the most effective ways for accessing other language libraries

!SLIDE bullets incremental
# Why I am excited about Mirah #

* easiest way to use JVM goodness 
* execute my code on highly tuned and enterprise acceptable virtual machine
* can use goodness of jconsole/jstack/jps
* mirah execution performance is at par with code written in java
* beautiful code

!SLIDE bullets incremental
# Why I am excited about Mirah #

* bytecode size is equivalent to code written in java, and far smaller than jruby
* mirah syntax is very similar to ruby and is often upto 50% lesser than a comparable java statement
* both interpreter and compiler are available
* No language-imposed runtime library
* Extensible Language

!SLIDE  commandline incremental

# Mirah Installation #

<pre><code> #download from https://github.com/mirah/mirah/downloads </code></pre>

<pre><code> rvm use jruby # I have rvm installed
=> Using /Users/senthil/.rvm/gems/jruby-1.5.6
</code>
<code> gem install mirah
=>Successfully installed mirah-0.0.7-java
1 gem installed
</code>
<code> mirah -v
Mirah v0.0.7
</code></pre>

!SLIDE  commandline incremental 

# Hello World #
<pre><code> mirah -e 'puts "hello world"'
hello world
</code>
<code> #generate the jvm bytecode from above example
</code>
<code>  mirahc -e 'puts "hello world"'
Parsing...
  &lt;inline script\&gt;
Inferring types...
Compiling...
  DashE
Done!
</code>
<code> ls *.class
DashE.class
</code>
<code> java DashE
hello world
</code></pre>	


!SLIDE  commandline incremental 
# how does it work? #
<pre><code> mirahc -j -e 'puts "hello world"'
Parsing...
  &lt;inline script\&gt;
Inferring types...
Compiling...
  DashE
Done!
</code>
<code> ls *.java
DashE.java	
</code>	
<code> cat DashE.java 
// Generated from DashE
public class DashE extends java.lang.Object {
  public static void main(java.lang.String[] argv) {
   java.io.PrintStream temp$1 = java.lang.System.out;
   temp$1.println("hello world");
  }
}	
</code></pre>

!SLIDE  commandline incremental
# Fibonacci #
<pre><code> cat fibbonacci.mirah
	def fib(a:int):int
	   if a &lt; 2
	     a
	   else
	     fib(a - 1) + fib(a - 2)
	   end
	 end
	
puts fib(10)	
</code></pre>
<pre><code> mirah fibbonacci.mirah
55</code></pre>

!SLIDE  commandline incremental 
# fetch ARGV #
<pre><code> cat argv.mirah
class MirahMainTest 
 def self.main(argv:String[]):void 
puts "hello " + argv[0] 
end 
end
</code></pre>
<pre><code> mirahc argv.mirah; java MirahMainTest Senthil
....
hello Senthil</code></pre>

!SLIDE  commandline
# class #
<pre><code> cat foo.mirah
class Foo
  def initialize
    puts 'constructor'
    @hello = 'Hello, '
  end

  def hello(a:string)
    puts @hello; puts a
  end
end

Foo.new.hello('Mirah')
</code></pre>
<pre><code> mirah foo.mirah
constructor
Hello, 
Mirah
	</code></pre>



!SLIDE  commandline
# classes #
<pre><code> cat class.mirah
class A
  def foo
    puts "foo"
    self
  end

  def bar:void
    puts "bar"
  end
end

class B &lt; A
end

y = A.new.foo  # y is an A
x = B.new.bar  # x is a B
</code></pre>