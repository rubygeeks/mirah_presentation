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


!SLIDE  commandline incremental smaller

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

!SLIDE  commandline incremental smaller

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


!SLIDE  commandline incremental smaller
# how does it work? #


!SLIDE  commandline incremental smaller

!SLIDE  commandline incremental smaller
