---
layout: post
title:  "Build Large Flask Apps in the Real World"
date:   2014-10-19 09:57:00 -0800
categories: software
---
Scaling a [Flask](http://flask.pocoo.org/) application is no immediately obvious
matter. At plug.dj we had ~22,000 line Flask application. At my previous
employer our Flask application was significantly larger. Ultimately scaling a
code-base is less about the framework used and more about the software design
experience of the developers working on it. Scaling in terms concurrent users
also has little to do with the web framework and more to do with your
understanding of load-balancing, caching, databases, etc. That being said, what
have I learned about how to organize a Flask application to comfortably grow?

Firstly, [fbone](https://github.com/imwilsonxu/fbone) and
[flask-bones](https://github.com/cburmeister/flask-bones) are great first
approximations. If you're struggling to figure out how to structure your flask
application have a look at those and consider using either one as a template
that you can evolve to your needs. Also, I have to mention
[cookiecutter](https://github.com/audreyr/cookiecutter) as a tool for templating
the structure of python applications in general. In terms of the web application
itself you might also consider using
[Flask-Classy](https://pythonhosted.org/Flask-Classy/) to build out your views.

Beyond that I hestitate to dictate anything else. There's never a
one-size-fits-all solutions for complex real-world problems like this. There
will never be a substitute for thinking up-front, and deeply at that, about the
organization of your application. The first few organizational decisions will
have ripple effects throughout the lifetime of the code base. Bad decisions can
trap you into a corner. Good decisions can make previously difficult problems
much easier. So instead here are a few heuristics that I've used to kickstart
this process:

1. **Think about deployment**. How is it getting to the server? egg, wheel, rpm?
   Will there be [continuous integration](http://jenkins-ci.org/)? Are you using
   [salt](http://www.saltstack.com/) or [puppet](http://www.puppetlabs.com)? How
   you deploy your application will determine what kind of structure you need
   and what kind of supporting utilites you may or may not have to write.
2. **Think about app initialization**. Where is the entry point? How are
   components initialized and shared? If my user module needs a database
   connection how do I ensure that it always gets an initialized database
   connection? Do I use singletons? lazy loading? dependency injection? It
   depends, and you should always be willing to revisit this decision. Also
   think about how you'd do a deploy to a completely uninitailized environment.
   How do you initialize the database(s)? Is the app configured by environment
   variables or cfg files? How are those being shared and deployed?
3. **Think about resource lifetimes**. Make sure you understand how your
   database connections and other resources should be managed within a Flask
   application. Typically you should initialize a resource when a request comes
   in and tear it down before the response goes out. SQLAlchemy
   [explicitly covers](http://docs.sqlalchemy.org/en/rel_0_7/orm/session.html#using-thread-local-scope-with-web-applications)
   integration with web frameworks in its documentation.
4. **Organize by principle of least suprise**. Ask yourself, "How would I
   organize this so that someone using Notepad with a good grasp on the
   programming language would be able to find and edit any arbitrary component?"
   This is ultimately how your codebase will seem to every new person who
   encounters it. For example, if you are asked to modify the function that
   geocodes a location and you have no experience with a code base it's
   reasonable that you'd look in *app.geolocation.utils* as a first
   approximation. You'd be suprised if instead it were somewhere like
   *app.auth.models*. The first example follows the principle of least surprise.
   Reduce the mental strain on yourself and others by sensibly organizing
   components into well named modules.
5. **Think about testing**. A focus on testing can help you avoid sticky designs
   because they simply become untestable. Organize your tests along the same
   lines as your modules so that the corresponding tests for any chunk of code
   can easily be found.
6. **Think about logging**. Bugs are going to happen and you're going to need to
   gather the information to solve them. Come up with a logging strategy that
   covers your whole application and stick to it. You should be able to log data
   from anywhere in any module and the logs should indicate exactly where the
   data came from. In Python the best way to do this is to initialize a logger
   at the top of each .py file, that way you always have access to a logger from
   every module.
7. **Think about infrastructure changes**. One of the best design heuristics you
   can use is to imagine how you would build your application so that arbitrary
   third-party dependencies (databases, web frameworks, etc.) could be swapped
   out with minimal impact. As your application grows your infrastructure will
   change. You should be able to switch databases, web frameworks, or deploy
   code to mobile devices with minimal code changes. A good place to start in
   figuring out how to do this is the
   [Architecture The Lost Years](http://confreaks.com/videos/759-rubymidwest2011-keynote-architecture-the-lost-years)
   talk by Bob Martin.

Each of these topics could easily fill a blog post on its own. With Flask in
particular (2), (3), and (6) are crucial. Flask isn't like Ruby on Rails for a
reason. Flask is designed to be easy to get up and running. It also puts you
closer to WSGI. This, however, is a double-edged sword. It can make development
easier in areas where you know what you're doing while also making it easy to
shoot yourself in the foot in the areas where you don't.

In the end you should be aiming to design your application to depend on Flask as
little as possible. The framework shouldn't dictate your application design, and
microframeworks in particular try to avoid doing this as much as possible.
Recently even Flask has felt bulky. [Falcon](http://falconframework.org/) seems
like a good step in the direction of something smaller.