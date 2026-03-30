Async Python or Asyncio or

Asynchronous, programming in Python

is such a beautiful subject.

It explores Python in totally a

new aspect, a new perspective

and not only that, a lot of new

framework like FAST API, they

utilize this specialty of

asynchronous programming quite

beautifully.

They make these frameworks like

really a present day framework

and all the framework seems

like outdated in front of them

and, and the magic behind

everything is asynchronous

programming.

Asyncio or Async programming is

relatively a small concept

in the foundation part.

It's not that big

but the implementations are

so big and so wide that people have

written books dedicated on it.

Yep, the concept is

pretty interesting.

Now with every book that you see on

the syncio they actually starts with

threading and I consider threading

and multiprocessing as totally

different subject than the syncio

but of course they have to set the

premises.

So that's why most of the syncio

book that you're going to see

first of all starts with threads,

then work on the processes,

multiprocesses, the logs, the mutex

and all these things.

Good news for us, we have already

covered that in the last chapter.

So in case you haven't seen that

chapter, go ahead and first

talk about that chapter or

at least go through with this.

Now this is a prerequisites

for this section.

You cannot learn Async a without

getting a full depth

about the multi threading,

multiprocessing, the mutex, the lock

that Python provides and whole

bunch of other things.

So go ahead and watch that first in

this section we are going to learn

about Async Python programming and

from the very first video, this

video itself, you're going to

understand that why is it so

powerful and so much fun?

Not only that, I will walk you

through with hardly four or five

concepts and these concepts are

going to be our foundation stone

for everything in Asyncio and

surely you will understand every

bit of the code and I'm super

excited to introduce to you all

of this.

So let me take you onto the screen

and first let's discuss

that where we are, why we are

doing this and all of that.

Now before we go for the async

Python, first of all there is

one thing that you need to know

about multi, processing.

We have seen the multi threading,

but we also need to know that

while multi processing gives

us parallelism, sometimes we

don't need that much of overhead.

For I o bound task like reading

the files, querying

the database or hitting the API.

We can use asynchronous programming

to make our apps much faster,

much more scalable, without spawning

a new threads or processes.

So you are saying that, all right,

multiprocess and even the multi

threading, I have seen those

examples, I don't have to use any

one of them and still my program

is going to be scalable, much more

faster.

Yes, it will be and that's

what we are going to do.

And what kind of problems we

will be able to solve with the async

nature of the Python.

First of all examples like let's just

say you want to fetch 10 web pages,

you might be thinking, all

right, I have to do this with

multiprocessing or multi threading.

No, you can do all of this with async

and they will be equally faster.

Maybe you have to read from 20 files.

Yeah, you can also go

ahead and do that.

Maybe you have to send 100

HTTP requests or HTTPs request

doesn't really matter much.

All of this can be done easily with

the help of async, programming or

asynchronous programming in Python.

If you do all these tasks one by one,

your code is actually blocking.

So if you are sending the web

request, by the time you're sending

the web request, your main thread,

your main application where all the

process is running, it's actually

busy, so your code is actually

getting blocked.

It waits for each operation to.

Now with the asyncio, you can

actually fire off many tasks

concurrently using the async await

syntax, where Python handles a lot

of things in the background as well.

Now coming on to this,

with the asyncio, you don't need

to learn like thousands of concepts,

you just need to go through

with couple of them.

The first one is going to be async

as a keyword before defining

the definition of any function.

So the regular function comes up as

just the default, but the async

function comes up with async def.

And yes, it's available

directly in the Python.

No need to do

any special magic on that.

On top of that, what it does async,

it actually declares a coroutine.

All right, what is a coroutine?

Coroutine is nothing much,

it's just a special function.

It would not be wrong

to call it as special function.

The only feature that it

gives you is a special function

that can be paused.

Yeah, that's it.

So that's basically

your async function.

You're writing a function which

can be paused Whenever you want.

And it can do some things

in the behind the scene background.

Once the task is complete, it

can again take the mainstream.

And yes, there are concepts for

that whole thing is not automatic.

You know what is going

to do all of this.

Another concept that you're going

to see into this is await.

In order to use await,

your function needs to be async.

Without this it's not going to work.

What it does the whole job

of this await is pause.

It pauses the execution,

until the result is ready.

Pretty simple.

It makes sure that hey, whatever

you were doing, I'll not

actually exit the function.

Whatever other task.

I can do those other tasks, later on.

But I will hold here, I will wait.

It just literally sits like that.

Okay, keep on doing the work.

Like maybe you are retrieving some

values from the database so that you

can send those values to the front

end so you can actually await your

function that hey, until unless I

get some values from the database, I

am waiting here, I'm not going to do

anything.

And this actually brings question to

a lot of people that I thought async

programming simply means that hey,

I can do things in the background.

And I'm okay with that.

Let's just say there is

a database request.

I can make that request behind

the scene or in the back end

and I can do my work.

But no async await.

This is where exactly async await

confuses a lot of people.

The whole idea of declaring

a coroutine is not to do

the things behind the scene

but but actually gracefully wait

for some things to happen.

While you can serve other

request and do other tasks as well.

But the task that you're doing,

the coroutine that you're doing

is not going to be completed.

Let me show you by more

diagrams of that.

So let's just say this

is your web server.

Somebody a user.

So let's just say a user

comes to you user.

And here's a user.

Nice one.

So here's a user which comes to you.

And there could be many users

that comes to your web server.

This user goes ahead and says

hey, I want to ask you

something from the database.

This is your async function

which went to the database

and says hey, I'll grab some

values from the database.

But by declaring these async

definition we are actually

not declaring a function, we

are declaring a coroutine.

That means that this function while

is busy in getting

some data from the database.

You can actually the same

coroutine can actually serve

to this function as well and it can

work absolutely fine for it.

It can make another

web request for it.

So this asynchronous nature

is really the backbone.

I will come back onto

this, don't you worry.

Right now just assume that async

gives you a coroutine which

are special function which can

be paused until and you can

do a lot of work on there.

Await is the keyword which

helps you to pause the execution

until you are ready.

And then on top of that we have

Asyncio which is a built in library

in the Python which provides you all

of this asynchronous function.

I'll just call this one as

built in Python library.

All right, seems good

enough, decent enough.

There we go.

And last but not the least,

this is the most important guy which

you don't touch by the code.

It automatically happens.

But this is event loop.

Now in case you're coming up from

the JavaScript ecosystem, event loop

is exactly same here as well.

There is no difference in the Python

event loop or the JavaScript.

The functionality, the foundation,

the core is exactly same.

But in case you are studying this

for the first time, don't you worry,

this is the engine that runs

and schedule coroutines in Python.

So let's just say I have declared

a definition a synchronous function.

Now this function is going ahead

and getting some of the data while

another user made a request to you.

Now this event loop is responsible

that okay, you were there

while getting some of the data,

I can come back to you and start

executing rest of the things.

But by the way event loop is one

of the most greatest thing of all.

I will show you some things

what happens in that.

So I'll go ahead and search on this

Python event loop and hopefully

I don't have to show you

the JavaScript version of it.

I don't want to do this, but this

is how the event loop looks like.

So it just takes everything

and put that into the queue so

that you can just go ahead

and keep on working your task.

And once the task is complete, this

is event loop is responsible to

take back that execution and start

that on the main thread again.

Otherwise you are just waiting who

is putting you back into the queue

that okay, you need to execute.

Now once a function stops,

that's it, it stops.

You can never resume a function until

unless you are doing the yield work.

But that's a different one.

But once the function is done,

it just keeps on executing.

There is no way

of Stopping the function.

The only way, how you stop

a function is to put that

into some kind of a queue.

This is known as event queue.

Now your event loop constantly checks

this event queue and whoever

the functions that got into it or

got resumed or whatever happens.

This event loop is the mechanism

which constantly checks

the event queue that, hey, is there

somebody I need to execute?

Is there somebody I need to execute?

And this is how it works.

It's a, pretty simple, pretty basic

and pretty foundational stuff.

They have a lot of diagrams

that works on that.

They don't really.

Some of them are great, some

of them are not really that great.

So notice here, this

is the event loop.

Oh, that's a beautiful diagram.

So notice here, this

is our main function.

It schedules back and everything

again, don't need

to too much worry on that.

I will show you how this

actually works and you will

actually understand the things.

Now it's time that we write the code.

If you will go into the diagrams

and theories and all these

things, you will never be able

to understand what's going

on and how is it going on.

Let me show you the interesting part

of it.

Let's go on to the code part

and call this one as simply 1 Py.

In fact, I will call this

one as 01 async 1 Py.

That's a good one.

The first thing that we can do is

go ahead and bring the asyncio.

This is the package and it's

built in, in the Python.

Now let's go ahead

and define a coroutine.

This is how we define a function.

But if I go ahead and say async,

that's a coroutine, that's it.

No other difference is there,

your parameters, Everything

remains exactly same.

Let's just say I want

to call this one as brew Chai.

This is the bare minimum of it.

All right, now, basic method

which prints it, brewing chai

with of course three dots.

And after that, here is

the interesting thing.

What I want to do is I want

to say await and I will say

here is async IO and it

also has a method for sleep.

All right, previously we

were doing time sleep, now

we are doing async sleep.

Don't worry, I will walk you through

what's the difference between them.

The difference is in

the foundation, how the code runs.

It feels like exactly same, but how

code works behind the scene, that is

what makes us a Python programmer.

All right, looks good.

And we're going to say chai is ready.

All right, now how do we

Go ahead and run this.

That's also interesting

since this is an async function.

You have to come up with

the asyncio and have to say

I want to run something.

What do you want to run?

I would like to run

the brew chai method and just

go ahead and run this.

You can do this in the main

methods and stuff.

There are lots of ways

of how people do it.

But what I want to show you is how to

run multiple coroutines and stuff.

Don't worry, we will

do this one by one.

All right, first of all,

let's go ahead and run this.

Don't want this one here.

Let's open the terminal here.

All right, this one is Python.

Please go ahead and run the 01 file.

And there we go.

It's brewing chai.

We wait for some time

and then says chai is ready.

But hey, what happened?

We used to wait for the time as well.

This is also waiting for two seconds.

So what's the difference?

The await keyword here is a non

blocking way to simulate awaiting,

for example a networking call.

So it doesn't actually block

the entire main thread itself.

Yes, it will allow you

to wait for a few seconds.

Assume this as a database operation

or writing something file.

But what it does these

async and await, it doesn't

block your main thread.

The reason why some

of the applications in JavaScript

and Node JS are super fast

is exactly this reason.

The reason why fastapi is so much

faster and it performs really well

is just because of this asyncio.

Asyncio is the whole backbone

of this kind of program.

Now let's see that how

we can actually run

multiple of the coroutine.

I'm pretty sure you are interested

in that part as well.

This is a very basic example,

but we need to do the basics first.

All right, let's go ahead

and call this1 as async2py.

All right, starts same.

You go ahead and say hey,

we get the asyncio.

We go ahead and say async Async.

Come on, I can write that async.

Let's create a simple

function that says brew.

Therehere we go.

Brew expects that you will provide me

a name of some of the chai and then

we'll go ahead and say print.

Let's use formatted

string and say brewing.

Whatever the chai or the name of

the chai you are brewing of course

with triple dots that is compulsory.

Now I'll again go ahead and do await

because I have async I can do await.

Otherwise I can do this.

Now I'll use the sleep operation

again for two seconds.

Good enough.

And then, we can go ahead

and get the duplicate of this.

And I can say I should actually

change the whole message.

And we'll say name is ready

with triple dots.

There we go.

So this is the basic

method that we have.

Let's say we have another one because

we want to learn how to write, how

to run multiple of the coroutines.

And this is our main.

Yeah, main can also be a coroutine.

There is no such thing.

Now here, what we're going

to do is we are going to go ahead

and say, I want to await.

And you can actually await

multiple calls as well.

Let me show you that.

So this is my async.

IO it has so many methods.

Notice here there's no shortage

of these methods.

Each one of them have

their own advantage and all working

on their own.

But majorly, you'll be using

sleeps and all, whatever

I'm teaching you here.

So I'll just go ahead

and gather this.

So now this method takes a lot of,

okay, coroutines.

So notice here it says coroutine

will be wrapped in a future

and schedule in the event loop.

Notice here they also mention this.

So this is our coroutine.

And you can actually wrap multiple

of the coroutines and will

be scheduled in the event loop.

They will not necessarily be

scheduled in the same order.

So order can change.

That's okay.

All future must share

the same event loop.

So basically what they're saying is

that you don't have to worry.

They are not going

to block your main.

They will not be

a blocking operation.

Other people can come

in and can still use our stuff,

whatever the methods and everything

that we are declaring.

But now let's see how we can do that

in here.

All I have to do is use this

brew method and say I want

to prepare different chais.

So masala chai.

What else?

We can have, we can have green chai

and we have ginger chai as well.

Once this is all done.

And I should have a comma.

That's why it's yelling let's.

For the housekeeping, let's

keep a comma here as well.

And once this is all done,

then I have to use the asyncio

and I have to say I want to run.

What do you want to run?

I want to run the main method.

That's it.

It's a really, really beautiful code.

And we will Just work on this.

Now how much weight

I should be doing.

There's one guy.

Assume that these are web

requests that are coming in.

So one guy wants masala chai.

You go ahead, get the chai

from the database.

It takes two seconds.

Then another one goes ahead and say

I want to get a green chai.

It waits for two seconds.

All right, so by the time

this third guy comes, we

have two seconds of delay.

Two seconds of delay

and finally we'll get this

after two seconds of delay.

But here's the interesting thing.

Let's go ahead and run this.

We'll go ahead and say Python

3, please run the second file.

And there we go.

Notice here it says

brewing masala chai.

We should be getting

the time as well.

But you have noticed here, and I

will show you again,

that you didn't actually waited too

much, you just waited combinedly

2 second only because this

was a non blocking operation.

And to just give you more idea,

I think 3 second is good.

Pretty good.

Sweet spot in the videos.

You wait for it.

All of them comes at the same time.

Because why non blocking operation?

Now this gives you an idea that all

right, things can actually go ahead

and change when you use the time.

So can we use the time as well?

Let's go ahead and try

this import time.

And instead of this line let's go

ahead and say time sleep and this

one sleeps for three seconds.

Fair enough.

Now can we go ahead and use it

because we are not using Await.

Let's go ahead and try this.

This is going to be fun.

So notice here brewing masala

chai, you wait for two second,

then you take another request

from the web and it's brewing

the green chai pretty good.

Now you see that

why fast API is super fast.

Yeah, that's the reason.

Async and Await, it actually

improves your speed significantly.

But what happens?

Majority of the people think that.

All right, await means I

will have to never wait.

No, await exactly means you will

wait, but in a non blocking fashion.

Hope this was a good.

All right, so should we

have one more example?

I think yeah, why not?

Let's have.

If we are doing this much, let's

have one more example on Async.

Await.

Definitely there is more.

I will come back onto the future

videos on this one as well.

Don't you worry on that part.

I know this is one of the most

fun stuff to do here.

We are onto the 03.

I'll go ahead and say async, async 3.

There we go, all right, so

this time let's just say we

want to fetch a request.

All right, so to fetch the request,

of course, if we are

fetching the multiple requests,

there is this website.

I should actually,

build my own for this as well.

Notice Here, this is HTTP

bin.org and delay two.

It gives you a two seconds of delay.

You can go ahead and add three.

And notice it, this is going

to give me a three seconds of delay.

We can use this to mimic

a simple operation that my

endpoint or my controller

takes 2 seconds or 3 seconds of time

to do some operation.

I don't know what operation,

but it takes some time.

And you can go ahead and see.

I can go ahead and give five, which

will be a really, really long time.

So notice here too much of this,

but I can actually go ahead

and get a decent time if,

I go ahead and Change this to 2.

There we go.

For the 2 request or the 2 second.

Now the request is all done.

I hope you can see that at the very

top, by the way, you can rewind

the 10 seconds and see that.

All right, in the two

seconds we get the data.

All right, so this is

the endpoint that I want to hit.

So copy that.

Let's go back.

And here's the interesting part.

First of all, come on, write it.

I will go ahead and import asyncio.

I will also go ahead and import

one more, which is, IO aio.

There is aio files,

but there is aio HTTP.

I probably need to install it.

I wish it could be already there.

So no worries, we can actually

go ahead and install it.

Let's go ahead and create

a virtual environment.

We usually do, but we

got bit lazy in this one.

So mvenv, venv.

You can use dot as well.

No problem.

And once I'm inside this, I'll

go ahead and activate this.

V, E and V.

Come on V E and V E and V.

Okay, and then we have bin.

Am I not writing it correct?

Venv slash.

Bin slash.

Oh, so source.

Why am I not getting this?

I'll just close this

and start it again.

You might be thinking,

all right, that's a lot.

Yeah, it is.

So I'll go ahead and say,

hey, source, go into venv slash bin.

All right, we have this one.

Activate.

Now, this squiggly line will not go

away because my Python environment

will not be able to detect it.

But that's okay.

I can go ahead and first say Python.

I want to install

pip, but it's already there.

So I know it's going

to be upgrading that.

Pretty simple.

And it's not like that.

My bad.

PIP install, sorry,

happens even to the best of us.

And then I can go ahead

and say PIP install.

And what I want is asyncio HTTP.

By the way, there are a lot of them

Asyncio HTTP, asyncio for files.

A lot of things you can do.

And there we go.

If you want to study more about it,

let's go on to the Google and we

can say asyncio HTTP and this is

the one that we are going through.

This is asynchronous, web request.

Yes, we have seen with the request,

we have done so many projects,

but this is how you install it.

There is AIO DNS, there is AIO HTTP.

So a lot of these things are there

server examples.

We can build our servers and all

things, but we are going to keep it

pretty basic, pretty short,

not too much of intensity here.

All right, so first of all now

what I can do is I can use

async and can define coroutine.

Now in the world of Python, if you

don't call them coroutine and call

them as a sync function, that

is totally, totally acceptable

in fact in the corporate systems.

And when you know your colleagues,

calling this as just

a function is also totally fine.

Don't get too much sweat on that.

Let's just say we fetch a URL

and for fetching this URL, you need

a session and you need a URL.

This is how it works by the way.

You can see and look

into the docs as well.

It's pretty simple.

Now with the async

in the asynchronous manner,

you can actually go ahead

and use with as well.

So notice here we have a session.

The session is like

you can make get request, post

request and all of them.

So this is a get request

and we'll pass on a URL

and we will get as response.

I know the syntax is bit

weird, but what can I do?

This is actually mentioned up

here that how you go ahead and use

their docs are pretty easy.

And this is where you can see

about making a request.

So notice here, this

is what I'm doing.

You can have the client session

as well as session or you

can have just the session.

That's totally okay,

we'll work on this one.

We are creating a wrapper,

function first, but notice your

session get, then you

provide this get the response.

I'm doing exactly the same thing.

Nothing is Coming out

of thin air, everything is coming

from the docs itself.

I will go ahead and print this

in the formatted string and all

we are going to say is fetched

whatever is the URL given to me

with status and I want to get

the status of response dot

status.

That's it.

Let me move this so we

got the status here.

Now what we can do is similarly

we can define a main method.

So async.

This one is going to be

a simple main method.

Forgot this.

All right, so first

of all let's give it a URL.

Yurls.

We can actually give three URLs.

But let's just say we

want to give it one.

We can give multiple request

URL for that as well.

But anyways, I'll show

you a nice trick.

We can have this and we can

say hey, multiplied by three

so it will store three.

All of them have two seconds delay.

We can use a variable and give

them incremental delay as.

Anyways, I'll not go too

much in depth of it.

We have seen that all.

Now with the async, I can say with

and I can say async IO HTTP.

This has the client session,

no suggestion aio HTTP.

Oh, it's not recognizing it.

That's why it's not giving

me the suggestion.

Otherwise it usually gives.

No worries.

We can actually go

ahead and grab this.

This is exactly what we want.

In fact we can say give me

everything, Copy that, paste that we

have a client session as session.

And with this session what

I can do is fetch the URL.

So I can just go ahead and say

I should actually be

saying this in comprehension.

And I can say here is

for URL in URLs.

What do I want to do?

I want to fetch a request.

So I'll go ahead and say fetch URL.

Call this one, provide the session

to it and provide the URL to it.

And I hope now you appreciate

that how we learned about

the comprehension, the strategies

to write them makes them

absolutely breeze now.

All right, so this will be my tasks,

all the tasks that I have done.

And after that, once this is

all done, I can just go ahead

and await, await till all

the tasks are being done.

But are we going to wait for

two seconds or six seconds?

That's the question.

And that's what makes it

is it a good one or not?

And here also you have

a method of gather.

Now we can gather all the tasks.

So we'll gather a reference of tasks.

All right, good enough.

By the way, just let me

know in the comments.

What is this asterisk?

Why does it come from?

Do they also mention this?

Probably not.

Probably not.

All right, so once we have this one.

Now here's the interesting part.

Don't worry, you will

understand everything.

Asyncio run and we'll have the main.

There we go.

So how much are we going

to wait for this one?

That's the interesting part.

Let's go ahead and say hey Python,

I don't need to say Python 3,

I can say just Python.

I'm in virtual environment,

get this, it sends the request,

it's constantly sending.

Two second is a lot.

But notice here we got all of them

almost at the same time back.

And that's all thanks to the async

nature asyncio of the Python.

Now one of the most interesting thing

that we need to discuss here is.

Let me just take you on here.

First of all, there is this

very big concept of blocking

versus non blocking.

This is the whole reason

why asyncio exists.

It's not about taking the things

in the background or

front end or whatever.

Our main thread needs to get

busy, but not all the time.

If it is busy in doing some

of the task,

other people should not wait.

They can actually asynchronously

call the same method.

And if somebody is already

doing the task, we can also

just get free in that.

That's the whole reason

blocking versus non blocking.

And also make sure that you

understand that what is a blocking

and what is a non blocking.

So whenever you go ahead and say

things like time.sleep and these

are just one example, there are

many such example time sleep

for two seconds or whatever seconds.

This is a blocking operation.

But once you go ahead and say that

I want to have a non blocking

operation, non blocking, then how do

you actually go work with that?

As of now there are many

others library as well.

But when you say await

async, Asyncio sleep.

This is a non blocking operation.

So that's the difference.

This one is a blocking one,

this is a non blocking one.

All right, one more thing.

I know some of you are worried

on that part, but I'll not

leave you on the cliffhanger.

I know some of you who

didn't pay much attention.

What is this asterisk talk?

I have never seen that.

All right, I get it, I get it.

This asterisk task is a really

interesting way of the things.

What you will notice that when

you are making a web request,

you are actually making a web

request to the multiple URLs.

Specifically in the array,

we have three values.

So the request, the response

for the three request

will also come in an array.

So the three requests will

become coming up to us.

So technically it will

be something like this.

So we have this tasks and this

task is going to look

like a T1, a T2 and a T3.

It's all in the array.

So it's almost like saying same that

if I want to do these things I have

to say something like T1, T2 and T3.

Instead of doing each of them

just like this, I happen

to just unpack them all the go.

So this is just a shorthand notation

for unpacking things in the Python.

So if you know that, all right,

multiple of the things are coming

up, so I'll just want to unpack them

because I'm gathering them anyways.

I can also go ahead and use

this, but I have to change

the syntax a, tiny bit.

I have to individually

capture all of them.

So this is a common syntax.

You're going to see that if there

are multiple requests, especially in

this format, then Instead of saying

t1, t2, t3 while using the gather,

we can just say asterisk task.

It just unpacks the thing.

It's like a spread

operator of Python.

But yeah, it unpacks the thing.

So hopefully that now

satisfies you that.

All right, I know that this

is how things are going

to be behind the scene, so I

can unpack them directly.

All right.

Quite a long video,

for this one, but I have a lot

more to discuss on this.

This is just the brief overview

the basic that we

have started in the sync.

It's such an interesting topic

and subject, but hope this video has

given you enough of idea about how

things actually work in Asyncio.

Super happy to have this.

Now let's move on to the next

**video and let's catch up there.**



Here is a very interesting take.

Can Asyncio and multithreading

also work in simultaneously?

Turns out, yes, they can.

And I'll keep the video short.

Just wanted to introduce you

that it's not like we are

leaving behind the multithreading

and multi processing.

That's not the case.

Asyncio is another tool in the belt.

We want to use it at its full

advantage, but we also don't

want to leave multithreading

and multi processing.

So let me take you onto the code

screen and show you a really,

simple example where we both are

going to have, threading mixed

with a syncio and I'll show you

what's the difference between

them.

The difference is in the concept.

It doesn't seem much in the output

and all of that, but it's behind

the scene what gets changed.

I'll go ahead and create a new file.

Let's call this one as zero,

four, and we're going

to call this one as thread async.

Py looks good.

All right, so the step one is

to bring your, classic Asyncio.

No problem there.

We also going to import the time

because why not?

We want to measure some

of the times and delays and whatnot.

Apart from this, we are also going

to, include, some of the things

known as concurrent futures.

I'll talk about them

in a second as well.

But first of all, let me bring that.

So there is something

known as concurrent.

Yep.

And in that you have

something known as futures.

Now notice here, it executes

the computation asynchronously

using threads or process.

The keyword here is asynchronously.

All right, so we are going

to bring concurrent futures.

And what do we want to bring?

It's a big module and as you can see,

there's so much thing all completed

broken Executor and all of them.

Well, the common thing that

you're going to bring in here

is thread pool executor.

It can execute, as the name

suggests, it can execute

all the threads in the pool.

In case you forgot just before this

notice here we have, not here.

In this one we have Asyncio.

Gather it's almost similar

to that, but for the threads.

Okay, now moving on.

Once we have all the details and all

the importing being done, let's go

ahead and create a simple function.

No async this time.

So it's not a coroutine,

it's a simple function.

Let's go ahead and call

this one as checkstock.

So let's simulate that if you ask it

for any item, it goes in

the database, brings in the value,

make the query on the database

and gets the value for it.

So I'll first of all print

up a simple statement that

checking item in store store

with dot, of course.

And then it uses the time module.

Because I'm not a sync here, so

I'll just go ahead and sleep.

How much time?

3 second seems to be good enough.

And make sure that you understand

that this is actually

a blocking operation.

It's not asynchronous.

It will block our main thread.

Once this is all done, I go

ahead and return something.

So I'll return a simple formatted

string which says item stock.

We don't have a database,

so I'll just go ahead

and say 42 for some reason.

So this item, whatever

the item you ask, we always

have 42 items of that.

Okay, now here is where

we define the async.

So notice here one function

is not async, but another

function is async.

We define this coroutine basically

and we have the main

method just like that.

So once we have this main

method, what I want to do is

first of all from the asyncio,

I want to get this.

So notice here we have the get event

loop and running loop and whatnot.

What we are interested in

in this case is the running loop.

Yep, get running loop.

Notice here returns

the running event loop.

Raised a runtime error.

If there is none.

This function is a thread specific.

So yes, async is not a replacement

of thread, neither a replacement of,

the processes as well.

It simply says that if your

application already uses threads or

processes, I can make them easier

for you, I can make them faster, I

can make them more compatible.

And that's what does the get running

loop is a method which is

specifically designed for threads.

Yep, let's go ahead

and work with that.

And what you do is this is a big

function or an object itself.

You go ahead and say

give me a loop from it.

So this is a get running loop.

Just like we have an event loop.

This is kind of a running

loop but for the threads.

Now once we have this, now I can use

the thread pool executor which will

execute the thread one by one.

And I will call this as pool.

Just like we open

the files just like that.

And now I can use await because

I am a sync and I can call

this loop that hey loop.

It has a lot of methods.

As soon as you put up a dot

you can see so many methods.

Call later, call soon, call soon.

Thread safe.

All these methods are available.

What I'm interested is running,

running forever run in Executor,

run until complete is running.

I can check the status

and all these things.

Now which one to use depends on

what you're performing, how

your application is using

these asynchronous, method.

Again these are bit

of advanced topics.

So if you don't realize, I

don't know which one to use.

That's okay.

That's totally okay.

When you will need them, you will

actually come back automatically

here and you will realize,

okay, this is what this method does

if I'm using that library.

So I will be using runinexecutor.

Now what this does, it constantly

executes the threads.

That's it, super basic.

And here I can say that, okay,

what do you want to do?

I have this pool, the first

option that needs to be passed on.

After that, where should

I target my method?

This is where you say check stock.

And what do you want to check?

This is like args.

Yep.

So we want to check for masala chai.

All right, seems decent.

And once this is all done,

let's hold the result into this

and finally I want to print

whatever is the result.

There we go.

And finally, last but not the least,

I have the asyncio which is

going to run the main method.

So I hope you can see

and notice this here that.

All right, we were having

this very basic method which was

blocking here.

Now what this?

Run Executor.

This is the main hero here.

The run in Executor.

The run in Executor lets

Asyncio run a sync function.

But.

But in another thread,

how beautiful that is.

We're not touching the main thread.

This program was not ready for it.

But Asyncio somehow beautifully has

this method run in Executor, which

specifically takes the threads only

and run them in a separate thread.

This is really

the most beautiful thing.

If you are at that point where you

understand the Python and see

the syntax, that this is beautiful.

That's why everybody

loves Async Python.

All right, let me show

you what it does.

It's not going to be

getting much of the result.

Its result is basic.

But the concept that we have studied

is actually very interesting.

So Python04 go with that.

And all right, so we

have some of the issue.

Looks like type object does not

support Context Manager protocol.

Looks like there is an issue.

Let me fix that.

My bad, I forgot a syntax here.

So notice here it says

with thread Pool Executor as pool

the type object does not

support the context manager.

So what, we actually forgot this

thread Pool Executor works like this

and hopefully this will fix it.

Not sure, but let's

at least try this.

Let's run this.

There we go, checking masala

chai in the store and we

get the result after obviously

two or three seconds.

But the beauty is

how it is executing.

It's not blocking our main thread,

it's actually spinning up

a whole new another thread

and that's where this is executing.

And the whole reason why we are able

to do this is because we are

having this run in executor.

Again, for a beginner

to explain this that what's

happening behind the scene,

there is no meaning for it.

But once you understand that.

All right, I now see that why we are

using Fast API and why some things

are faster, why some things are

not faster and not that scalable.

These are the things which

are the reason behind that.

So I hope I was able to give

you some context and some standard

template code which you can use

in your code as well.

Whether you're doing machine

learning, data science or web

dev, these are really

interesting and they help you

to understand the existing code

base that you will be working

with the company.

Hope that's good.

Let's go ahead and catch

**up in the next video.**

Hey there everyone and welcome

to the Python course on Udemy.

In this video I will show you that

how you can utilize multiprocessing

along with the syncio.

In the previous video we saw

that how we can use multi threading

and use a syncio so that

it moves the consuming task

onto a separate thread itself.

And similar thing can be done

with the multiprocessing as well.

I'll show you one great use case

example as well to solidify

our learning and that's all

we'll be doing in this video.

Let me take you onto

the screen and show you

what we are about to do.

It's a very simple process and just

to give you a brief overview, in

the last video we saw that we can

have a check stock and we can use

thread pool executor and then can

use run in executor which actually

takes off your heavy duty task and

put this into a separate thread

altogether.

We want to do similar kind of

a thing but for process this time.

So let's create a new file,

call this one as 05 and this

one is actually processing.

So process async py

the starting of the process will

remain exactly same.

We will use the async IO

that's standard and we need

processes as well.

So from current concurrent

futures we want to import

the process pool executor.

This is the only guy who executes

the processes in a pool.

All right, so let's just say

the premises that we want to set

here is somebody gives you some data

and you want to encrypt that data.

So we will take the customer, credit

card or something and then we are

going to go ahead and encrypt that

some data or something like that.

So it's a CPU intensive task that

needs to run on its own process.

The whole summary is that

and we will be simulating this so

it's not going to be accurate.

So encrypt, this is the method, this

takes the data and somehow it takes

a lot of data and then it goes ahead

and returned this and I can just

return a simple formatted string

with a log sign that hey, whatever

the data you have given me that's

now logged and let's also go ahead

and do the data and for this data we

are going to go ahead and return

like nothing.

So we have already

discussed these things.

Nothing much.

Whatever you want

to return, you can do that.

Now here's the interesting part.

I will have the async

and we'll have the main method,

this is asynchronous.

So this is a coroutine that

we have in front of us.

And once I have this,

then first and foremost I will

create a running loop.

So I will say hey Asyncio,

just give me a get running loop.

So this is an event running loop.

We don't want that, we

want a running loop.

All right?

And we will hold the reference of

it in a loop variable,

straightforward and just like the

previous one, we are going to go

ahead and say process pool

executor and make sure you don't

do the mistake.

Use the parenthesis there

and use as pool.

And then all I have to do is use

await because this is going to work

onto a separate process altogether.

And I can use this loop to run.

And notice here there's run forever

Run in executor, run until complete.

We just want to run a simple

way run in Executor.

It requires a couple

of parameters to pass on.

The first one is, is that we want

to give it a pool as well.

So let's say this is the pool.

Remember the pool

in the line number nine.

That's the same one we are giving.

We need to give it a target as well.

So our target is encrypt the method

that we have designed and then

finally we'll give it some data.

So Data is credit card, 1, 2, 3, 4.

That's my secret card number here.

And once I'm done, what we're

going to do is hold this

into a result variable, simple.

And once I'm done with this, I'll go

ahead and just print the result.

And yeah, that's good enough.

Let's go ahead and print the result.

So that's it.

And last, you also know this, that

Asyncio, Asyncio, needs to run this

dot run and we have the main.

There we go.

So this is the basic.

The only difference is

by running it this way this is

much more of an asynchronous

operation and the result

is simple, the offload.

This actually goes ahead

and offloads the CPU heavy work

to another process

so it doesn't block the main event.

That's the whole goal

and that's the whole idea.

I'll show you one

implementation as well.

So we'll just go

ahead and close this.

We will have the Python.

Yep, we are

on the virtual environment.

This is the 05.

There we go.

Oops, we forgot to put

everything into main.

We forgot to have

the dunder main here.

So a process in the we have seen

this probably many times now.

Feature result.

What happened to you?

Futures Looks like there

is a different result or

Executor looks good.

Let me check the error and turns

out this looks like the same error

that we have seen in the past

whenever we deal with the processes.

This is kind of the same thing

which bugs us again and again.

So I think we can resolve this

by just cutting this out

and use the same thing.

If the dunder name is equals to

if it doesn't fix it, no worries,

we'll figure out the solution.

That's how you learn the code.

And there we go.

Should be fairly okay.

I'm not really a big fan

of the processes just

because of this reason.

Asyncio makes much more sense

and much more life easier.

But I know there are certain use

cases where you have to run

the things into a separate process.

That's okay, we get that.

So let's try to run this again.

And there we go.

Now it works.

So notice here how we are actually

returning the values just like this.

So it's encrypted.

Somewhat encrypted,

not really encrypted.

But at least now we are able

to run the program here.

So this is the basics

of how it works.

And again, always be cautious that

if you're using the processes,

this main routine is required.

Otherwise the things get really

nasty because nobody knows that

what main thread is running,

which is the leading event, which

is running the whole thing.

And if I finish my process

where I need to get back.

So there needs to be a marking

of the main thread which is going

on or in this case the main process.

So I hope this is good.

But we'll also do one more operation.

So to give you a brief

kind of simulation of where

it could be useful.

So let's build a kind

of a logger which logs something

every second, not in the file

but just on the terminal.

So we'll just do this just

for a fun, an impromptu just to make

sure we are having fun with

learning the python so 06 and let's

call this as bgworker py.

All right, the process is simple.

We're going to go ahead

and bring in Async IO.

We'll also go ahead and import

the threading this time because

if I do this on the main

thread, my main thread will be busy

in just logging the event.

So I don't want to do that.

I want this to happen

into a separate thread.

This thread is responsible for

logging the events every X second.

And my asyncio can be totally

separate and do its job.

That's what I want to do.

So this is basic.

And now let's just say we

have a background worker.

Background worker.

This is a very common scenario.

All right, good enough.

What it does, it just

constantly works.

So we'll just go ahead and say true.

What happens into this while loop,

you go ahead and sleep

for one second and then after that

you go ahead and print some data.

So let's just go ahead and print

logging the system health.

For some reasons you are logging

the system health every second.

So let's go ahead and have a clock.

This one looks good.

All right, so our logger is ready.

Whatever is the definition.

And thereafter I can have

my async, operation.

Let's just say I want

to have a fetch order.

Fetch orders, which takes the order

and it's going to completely

going to take the orders.

And this is going to be await.

I can go ahead and say asyncio sleep.

And this one is

asynchronous in nature.

So I can just leave for three

seconds and then print that.

Hey, I was able to fetch the order.

So let's use a box.

Yeah, this looks like present.

So order fetched.

There we go.

Now how do we run this?

Now we want to run it not

just by simply running

the fetch order itself.

The way how we are going to run this.

First of all, we are going

to go ahead and get the threading

and get the thread ready.

And through this I'll say

there is a target for you

which is background worker.

Nice and easy.

And we're also going

to mark this as Demon True.

I'll talk more about the demon

True in the upcoming videos.

You can also learn about them.

If I'll get a chance.

I'll definitely talk about them.

There we go.

And we'll just go

ahead and start this.

There we go.

Nice and easy.

I'm hiding a little.

There we go.

Hope that's clear now.

Okay, once this is all done

now I can just go ahead and say,

hey, Asyncio, you go ahead and run.

What do you want to run?

I want to run the fetch orders.

All right, so notice here

what we have done or what

we are able to do here.

Now surely it's not that always

you have to use asyncio and inside

that only you have to do this.

What I'm doing is I'm running

my application in asynchronous

mode, but also My application

now have a separate thread

which is bothering nobody.

It constantly just logs

my system health.

That's it.

Now let's go ahead and run this.

And the best part is this.

Asyncio awaitsleep is not going

to bother this sleep.

This will constantly work.

Let's go ahead and see

that in action.

So this will be python06.

There we go.

So let's run this.

So this is logging the system,

but my order is being fetched.

So notice here we were not

being blocked by anybody.

Our fetch order were working,

our thread was working.

So this is one such example.

Now surely there could be other

things where things can actually

work or have other examples.

Maybe you can build something like

an interesting chai delivery SaaS

platform where asyncio takes or

talks to the third party like

Google Maps or Razorpay, while

there is a background

multiprocessing.

Probably simulate a machine learning

model, which predicts the T demand.

Again all fictitious.

Throw up some random data

after some time and you can also

use threads to keep the UIs

and the logs responsive.

Maybe log every single time that.

Okay, this system has been active

for this second and this second.

So try to design these

kinds of things.

The more you are going to code

in Asyncio, the better it is.

And if you happen to work in future

with things like fastapi, you

don't need to worry too much.

Fast API does everything,

Async, almost everything and it

teaches you so much more.

So, so that is it.

Hope you have enjoyed this.

It was a pretty decent,

fantastic video.

Hope you have enjoyed this.

And if you need anything more than

this course, just let me know.

It should be core foundation

of Python and I would love

to make more videos.

I do come live on YouTube, I do,

lots of spaces on Twitter as well.

Join me, let me know how can I make

this as a world's best course

on the core foundation of Python?

I would do everything that's possible

to make this

the world's best course.

That is it for this one.

**Let's catch up in the next one.**


Had to restart my computer

in between the recording.

It was.

The whole system was

up and running from months

and probably it was glitching.

Hey there everyone and welcome

to another video

on the Python course on Udemy.

And this is a very interesting video.

This video will walk you through

about the profiling as well as

some of the debugging that you

can do for the code that use

multi threading, coroutines,

multiprocessors and all these

things.

Now with this I would like

to break you that if you're watching

this video with expectation that

I will get a silver bullet that

will solve all of my problem.

No, it doesn't exist.

You need to be careful while

writing the code with the thread.

Now there are tools which can

do some of the profiling.

I will walk you through what

profiling is and there are certain

tools which can help you to debug

some of the issues in the memories.

And these are all third party tools,

like other developers developed them

and made it available absolutely

for free with the source code.

So they are pretty nice.

But there is no one way

that, hey, this will solve all

of my race condition.

This will solve all of this.

No, it doesn't happen.

You just need to be aware of a code

where such things might occur and

be careful with them and have the

knowledge of some of the tools

which can help you to prevent such

things.

That's it.

So with this, there is enough

in this video that will help you

to understand all these details.

So let me go and share

the screen with you

so that we can work on that.

Now first and foremost what we are

going to do is we are going to work

on the profiling and you might be

wondering what is this profiling?

Profiling is a very interesting

concept altogether.

So first of all let me go

ahead and switch into this.

Since I restarted my system,

I will go ahead and open this up.

Yep, we are in the right folder.

So source venv PIN activate.

There we go.

Now the first thing that I'm going

to show you is look at this code

that we saw in the previous video.

Very simple code, hardly

12 lines of code.

And we want to profile this code.

Now.

What do you mean

by profiling this code?

Now Python provides you some of the

tool for profiling and what it

does, it shows the time spent in

each function and it's really good

for the input output, based kind

of a function or computer heavy

memory, heavy compute, heavy kind

of a task.

Now what this profiling does, the

amount of methods that you have it

Will tell you that where my main

thread, main thread or any thread,

spend amount of time in each one of

them.

Based on that you can optimize

that particular method itself or

coroutine as well.

So how do we run this?

And it's actually super easy.

You can just go ahead and say

Python and provide a flash

of flag of And there is profile, C

profile and again

pay a small attention here.

The P is capital in here.

Then you have to provide

a S option of time.

It has many other options you can go

ahead and read in the docs for that.

And after that all you have to do

is say whatever is your script.

In this case it's a 08 script.

And let me warn you,

before I run this, the output

of this is not easily readable.

It requires trained eyes as well as

some of the senior capabilities who

can explain you what's going on.

And it takes a little

bit of the time.

This is not for beginners and in

fact things like profiling, writing

the code for multithreads and even

debugging the code for multithread

is not for somebody who is a

fresher or beginner or I would say

it's also not for somebody who has

been writing the code for two,

three years.

It requires years of experience.

So I'll just open this up and as

you can see, this is not really

the thing that you were expecting.

Yeah, this is how it looks like.

It's very barely readable.

If you go ahead and look

at this, this is how it looks

like and it tells you what

happens and what's going on.

As you can see, this is a lot.

This is a lot.

If I go ahead and get started here.

So this is the end calls,

total time, per call.

There's lot of them.

And again, finding and getting all

of them is not that easy.

But just wanted to show you that

yes, the tools like cprofile

exist and you can profile each

of the method that's available

to you and can work on with this.

So that's your basic profiling.

But now let me show you some of

the very interesting code that

you probably haven't seen and you

should not be seeing them as well

because if your code base has

this kind of a code, there's no

good way that this code reached

to you.

So this is known as first

of all, race condition.

What is race condition?

We have been talking all

about it for really long, but it's

actually not that hard.

All I can do is first of all I can

import the threading and let's just

say we have this variable called as

Chai stock having a zero value.

And let's just say we have a simple

method which restock the Chai stock.

There we go.

I take the reference of my global.

So I'll just go ahead and say in

the global give me the Chai stock.

All right, you got this one.

And then there is a loop

for something in range.

And how much range?

Probably hundred thousand.

Good enough.

And we go ahead and say Chai

stock gets a plus equals 1.

Pretty basic.

All right.

Now after that what do we

do is we simply go ahead

and say we want threads.

It will give you a pool of threads.

So this is how we'll write

a simple comprehension.

And I'll go ahead and say

for something in range

and we'll only grab the two.

What do I want to grab?

I want to create the threads.

All right, so threading dot thread.

And we will have a target.

The target is going to be restock.

Now this looks absolutely

innocent piece of code.

And we can also have

for T in threads.

What do I want to do?

I want to say T dot start again.

We can write comprehension as well

and we can write this way as well.

And then after that we

can have the T joins.

So this actually runs the code.

Very basic code, nothing

big deal up there.

And what's surprising is

this code is unpredictable.

It looks predictable

at first, but this code is

absolutely unpredictable.

So I'll just go ahead

and say Chai stock.

And what's the value

of the Chai stock?

The value is going to be Chai stock.

Now you might be thinking, hey, we

have seen this kind of a code.

It's not unpredictable.

It's going to just go ahead, two

threads will run this and we'll get.

The expected result is 200,000.

But that's where the problem is.

Let me just go ahead and run

this and see if we can get

those unpredictable result.

So Python, 09 and all we have

to do is run this again.

Again we have 200,000.

Please give me at least one

time unpredictable result.

Very hard to get

the unpredictable result in this.

Python is not allowing me.

I'm trying my best, but this is

actually an unpredictable code

in itself because you have no idea

which thread is going on and which

one is actually increasing this.

There is no locking mechanism,

nothing is going on.

It's just constantly going on that

although it didn't showed any

reliable result in our case, I tried

my best to run it so many times.

But, but that's the thing.

When you test it on the local host

system, it works absolutely fine.

But there is that one condition

where the race condition will happen

and the two threads will raise.

In between that I will

update it first.

I will update it first.

And you have no idea when that

one single flaw happened.

And even imagine if it is a stock

market or banking application,

that even one glitch,

might have less than the result,

than 200,000 or maybe more.

And in both cases you

are absolutely wrong.

So this is a common race condition

where what data we are modifying,

we have no control over it.

And which thread is controlling

it, we have no idea of it.

And this is known as race condition.

And again, showing the demo

of these things like race condition,

it's really, really impossible.

You just saw this.

But just because I was not able

to show you the demo, doesn't mean

you understand the concept.

You absolutely understand the concept

that, yes, this is a part where

this thread might be updating this,

and in between, this thread might

come up and just update the value.

So the value could be

higher or could be lower.

And in both cases we are

absolutely not happy.

So keep an eye.

This is a race condition.

You might want to avoid this.

Get the locks and everything

that I have gone through.

But when you introduce the lock,

there is another condition.

There is another thing

that can happen.

Let me show you that.

So let me open this

up and this one is 10.

So 10.

And this is known as deadlock.

I will write a very explicit

condition on deadlock.

You will not write such code.

But hey, things do happen

in programming.

So let's just say if I go

ahead and say I want

to import the threading.

Now let's go ahead

and acquire a lock.

So this is my lock A.

How do I acquire lock?

Threading gives me the lock.

So threading dot lock.

There we go.

And similarly, we can acquire

another lock as well,

and that could be thread B.

And again, I sometimes forget this.

This works like that.

There we go.

All right.

Now let's just say we have

a task one, no big deal.

We can have a task one all.

Right.

So task one, let's just say

we acquire a lock first.

So we say that, hey, with lock A,

I want to do some task.

I will go ahead and say print

and I will say task one.

Acquired lock A.

Pretty good no big deal.

Now, once I'm done with this,

within this lock, can I go ahead

and acquire another lock?

Yeah, you get the idea.

Yes, I can go ahead

and acquire a lock B as well.

So this is my lock B.

There we go.

And this one

now acquires another one.

So oops, we'll go ahead

and say there we go.

This one says that, hey, task

one acquired the lock B as well.

Okay, no big deal.

You start a task, you acquire a lock,

do some work, then you acquire

another lock and do another task.

But what if we do some kind

of a reverse thing here as well?

This, this task two and this

is written in another

file, another PR request.

Some of your colleague

is writing this.

And this time what you do

is you write the exact same

code but with a twist.

This time you go ahead and say, I

would like to acquire a lock B.

Okay, so you acquired a lock B

and then inside the B

you are acquiring a lock A.

And here you mentioned that.

Hey, now I'm going to go

ahead and acquire a lock A.

This is interesting.

And this is kind of a deadlock.

So let's go ahead and get two threads

Now.

Notice initially we were having

so much of the slowly going

on with the threads.

Now we are just writing

threads like it's anything.

That's what happen when you spend

a lot of time, doing one task.

So this is task one and this

is doing the task two.

Let's give them the name

for each one of them.

This is my thread one and this

is going to be my thread two.

There we go.

Now once we are done with

this, let's start Both the thread

T1 gets a start

and similarly T2 also gets a start.

Good enough.

What will happen in this case?

Again, the results are unpredictable.

They might work, they might

not work, but this is

a classic deadlock condition.

I'll go ahead and say, hey

Python, just go ahead

and run the 10 deadlock.

And there we go.

It says task one acquired lock a task

one acquired and it's waiting.

The task two is waiting that, hey,

leave this lock so that I can

also go ahead and acquire a lock.

This program is

in a deadlock in itself.

It will never exit, it will never,

go out anywhere else.

And even if I go ahead and show you,

this is actually for the task 2.

This is for the task 2.

This is not 3.

Definitely task 2.

This is a classic deadlock

condition and you don't know

which thread is going to go.

Notice here.

Task one acquired lock A

and task two acquired the lock B.

Both of them have acquired one lock

and nobody's leaving the lock.

This is really bad.

But this is an exaggerated case.

It's not like all

the cases goes like that.

And there is no easy way to find

out because here it's very clear

that okay, this is the condition.

But imagine if this is buried down

into a whole different module

of the Python, this is whole

different and you have no idea.

You don't have print statements.

Yes, you get it.

To solve these kinds of things,

logging is one of the such issues

that you can acquire.

So thread safe is logging.

You can also do enumeration

on the threads which

is itself in a topic.

Lots of books write about them.

But these are the basic things that

you can do now with this I would

also like to show you a couple

of tools which are available there.

So I'll just go ahead and open this

up and show you directly with this.

The first one is Pyspy.

It's a very popular one.

Pyspy.

So this is the one, the second

link, don't go for the first one.

Oh anyways, it's sponsored.

So this is a tool Pyspy.

It's a very popular tool for sampling

profiler for Python programs.

So it actually does is

profiling of your code.

One profiler I show you which is

with the default one but you can

go ahead and record all of them.

They give you this kind of a diagrams

as well that what module took

what time and how much it goes.

This one is a more professional

tool which I showed you.

Compared to that this

is much, much better.

But not only that, there is

another one which is also

open source and used quite

a lot, which is VProf.

VProf?

Yeah, it's a famous one,

the first one or probably I

have visited it many times.

That's why it's first one for me.

So VPROF is another one and it

also gives you crazy good

level of visualization.

You just saw this.

So this visualizations are

of the charts and pretty

fantastic tool.

There are others as well like

Thread Scope is there but I haven't

used them, touched them ever.

These are the ones which

I have minutely touched.

Not too much but yeah.

So in case you want to go more

on the profiling and debugging,

race conditions and all of that.

Yeah, these are the tools.

But again there is no silver

bullet to solve these things.

If you think that I will be able to

profile it, debug it and all of

that, you have to work and you

have to understand your code that

you are writing and you have to

maybe have a discussion with your

colleague.

Hey, this is what I'm doing.

This is where I'm acquiring

the lock, what you are doing.

Are we having a proper mutex or.

We are in the deadlock condition.

These things needs to be discussed

and then can only be handled.

That's the whole thing.

Hope you have enjoyed this video

and if yes, please do rate us.

It's very, very important for us.

And that's it for this video.


In the last video I showed you a word

demon and I'm pretty sure some

of you are wondering what is daemon?

Although this video was not

planned, but I don't want

to leave any stone unturned.

I want to teach every topic that's

there in the Python and daemon

and non demon threads is one

such topic which I teased

but didn't talk much about it.

So why not to have a video on it?

Let me take you onto the screen

itself and talk more

about that, how this actually

goes and work with this.

So all right, why this is

not sharing anything.

Looks like there's something wrong.

All right, fixed now.

Hopefully.

Excuse me on that.

Sometimes system misbehaves.

All right, so let's talk

about what is this?

So when you work with any threads

in Python, one subtle issue

that you may encounter,

sometimes only that your program may

exit before your thread finish.

So this thread here never

finishes, but this one definitely,

definitely finishes sometime.

So sometimes your threads finishes

up late or sometimes doesn't

finish at all because not all

threads are treated equally.

So what happens when

the main thread finishes?

What are these daemon

threads and how to use them?

How do they differ from

the non daemon threads?

There are a lot of questions

in your mind.

So let me just clear this up.

Let's create a fresh file and talk

about them directly.

Let's go ahead and create a new

file.07 will work on the daemon

and non daemon both the threads.

So daemon py that's enough.

So daemon threads are the threads

that are background threads

that automatically shut down

when the main program exit.

So these are used for non

critical background tasks like

logging and monitoring.

So you know the details and premises.

Now let's go ahead and write them.

So let's say we have a threading.

We also have a time.

Good enough.

And let's just say you are

monitoring something.

So monitor t temp.

It's monitoring the t temperature.

Simple simulation.

Now we are constantly monitoring it.

So while true is there and we

also print some message just

like this and what it does is

monitoring t temperature

and of course with three dots.

All right.

And it also goes ahead and sleep

for two seconds.

Obviously this is running

on the main thread.

If you run this method directly,

everything will

wait, nothing will happen.

But what we're going to do

instead of doing this we go

ahead and say that instead of

doing that let's take the

threading and have a thread and

once I have this thread let's

give it a target.

So, so target is monitor

T temperature and I'm

marking it as daemon.

Come on.

Why is it not suggesting daemon?

I misspelled this.

The file name as well.

My bad.

So I can just mark this as daemon.

True.

And again, as I mentioned, daemon

threads are background threads

that automatically shut down

when the main thread is gone.

So this is the whole definition,

not too difficult.

I'll just go ahead and say start.

There we go.

And we haven't stored this

into a variable,

so let's call this one as T.

So T start.

All right, and then we go

ahead and simply say

this is main program done.

Very strange piece of code.

Hope you get the idea that

why we are doing it.

First of all, this is bothering me,

so I'll go ahead and rename this.

Yeah, it's bothering me.

It's daemon.

Daemon py wow, second time

I did a miss a typo there.

Don't worry, behind me,

I'm just fixing the typos.

Demon.

There we go.

You can see at the top.

It was just bothering me.

Let's see what could be the output

of such a program.

Let me go ahead and open this up.

And there we go.

So we'll just go ahead and say Python

and this time we'll

run the 07 and there we go.

So it monitors the T temperature

and once it's being done,

that's it, it's done, it's gone.

Now can we go ahead and change

this a little bit?

Probably yes.

So let's go ahead and create

a new file for this.

We'll copy paste the code.

But I want to create new file

for this so that I can give you

all separated one zero eight.

This one is demon.

It's a non demon, non demon.

Py.

All right, so most of our code

will remain exactly same.

So let me go ahead and borrow this.

Copy this and let's paste this.

Now how can we make

it as a non daemon?

Just go ahead and remove this.

Pretty simple.

And that's it.

That's what it takes.

Now what's going to be

the difference in this one?

Let's see, by running the program

this time I want to run python.

This is 08 and there we go.

So notice here it says

monitoring the T temperature.

But your T temperature is

constantly getting monitored.

Because you asked it that.

Hey, it needs to run onto a thread

while your main thread was all done.

It is still monitoring

the temperature.

And yes, there are use

cases for it as well.

I'll not constantly run it

for the lifetime of it.

But hey, I was able to shut it down.

But you get the idea.

The possibility with the daemon

thread and non daemon threads

are really, really a lot.

And yes, there are cases

and possibility where you may

want to run it onto

a non daemon thread where it's

constantly keep on running.

So very simple concept, nothing

too much to worry about,

nothing too much to bother about.

It sounds a lot, but it is not.

Hope you have enjoyed this video.

**Let's catch up in the next.**
