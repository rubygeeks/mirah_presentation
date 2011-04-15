!SLIDE bullets incremental
# Why Mirah for Non-Java Programmers #

* Co-Founder and CEO of RailsFactory
* programmer at heart
* curious


!SLIDE bullets 
# Mirah Learning Resources  #

* [http://www.mirah.org/](http://www.mirah.org/)
* [http://groups.google.com/group/mirah](http://groups.google.com/group/mirah)
* [https://github.com/rubygeeks/mirah_book/](https://github.com/rubygeeks/mirah_book/)


!SLIDE  commandline incremental

# Mirah Installation #
<pre><code> rvm use jruby # I have rvm installed
=> Using /Users/senthil/.rvm/gems/jruby-1.5.6
</code>
<code> gem install mirah
=>Successfully installed mirah-0.0.7-java
1 gem installed
</code>
<code> mirah -v
Mirah v0.0.7
</code>	
</pre>

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
</code>
</pre>	


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
</code>
</pre>

!SLIDE  commandline incremental smaller

!SLIDE  commandline incremental smaller
