---
layout: post
status: publish
published: true
title: I miss my monkeypatch.
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 19
wordpress_url: http://beginsinwonder.com/2005/12/14/i-miss-my-monkeypatchif-you-have-done-a-decent/
date: '2005-12-14 04:02:00 -0500'
date_gmt: '2005-12-13 22:02:00 -0500'
categories:
- code
tags: []
comments: []
---
<p>I miss my monkeypatch.</p>
<p>If you have done a decent amount of python code, you've probably run into <a href="http://zopewiki.org/MonkeyPatch">monkey patching</a> - if you haven't, you're missing out. But in java, where I use an ever increasing number of open source libraries, I missed this lovely feature I was able to use to good effect in <a href="http://www.plone.org/">Plone</a>. But no more, now there is AspectJ to the rescue.</p>
<p>First off, the problem I had was to extend the code generation capabilities in Axis 1.3 to generate java code from a WSDL (which is better than the other way around). But <a href="http://ws.apache.org/axis/java/integration-guide.html#WSDLParserAndCodeGeneratorFramework">WSDL2Java extension is limited</a>, and I don't feel like downloading all the Axis source and changing it and recompiling it myself. All I wanted to do was to make the java code that was created include a unique ID to make the objects easier to persist in hibernate (and just to be a show-off, yes I am using Spring too, but not for code generation - it's not good for everything :).</p>
<p>So how to do it? Easy enough, use the <a href="http://www.onjava.com/pub/a/onjava/2004/10/20/springaop2.html?page=2">cuckoo's egg design pattern</a> to replace Axis's current java class generator with an instance of my own when the constructor is called:</p>
<pre>
import java.util.Vector;
import org.apache.axis.wsdl.symbolTable.TypeEntry;
import org.apache.axis.wsdl.toJava.Emitter;
import org.apache.axis.wsdl.toJava.JavaBeanWriter;
import org.apache.axis.wsdl.toJava.JavaWriter;
import org.kookster.PersistentJavaBeanWriter;

/**
* Use this to change the behaviour of the WSDL2Java axis code gen
*
* @author kookster
*/
public aspect ReplaceJavaBeanWriterAspect {

//here's a pointcut to get the public constructor of Axis JavaBeanWriter
public pointcut javaBeanWriterConstructor( Emitter emitter,
                                         TypeEntry type,
                                         Vector elements,
                                         TypeEntry extendType,
                                         Vector attributes,
                                         JavaWriter helper ):
  call( JavaBeanWriter.new( Emitter,TypeEntry,Vector,TypeEntry,Vector,JavaWriter )) &&amp;
  args( emitter,type,elements,extendType,attributes,helper );

//here is the advice which calls the constructor for my object instead
JavaBeanWriter around( Emitter emitter,
                      TypeEntry type,
                      Vector elements,
                      TypeEntry extendType,
                      Vector attributes,
                      JavaWriter helper) :
javaBeanWriterConstructor( emitter,type,elements,extendType,attributes,helper )
{
  return new PersistentJavaBeanWriter(emitter,type,elements,extendType,attributes,helper);
}

}
</pre>
<p><!--1e6c26011a85165ae8bbae20fb403e4c--><!--5e1f4c943e8d287cd6f532ed1dc8bdd7--></p>
