Hey there everyone, and welcome

to the chapter of concurrency

and parallelism in Python.

Now parallelism and concurrency are

closely related subject, but it's

very important that we understand

the difference between them,

segregate them and try to understand

why they are important.

When you first time look

at the whole picture of concurrency

and parallelism, you are going

to see that parallelism

is actually much better and we

should always use that.

But once you see them closely and

have a discussion on them, then

you start to realize that no, it's

not that fancy and it's not a

silver bullet to do all the tasks

and sometimes even parallelism

doesn't suit some of the process

to work on with.

They both have their own places

and their work and there's

some of the tasks and jobs

that needs to be done by exactly

that particular thing.

And also the concept

of parallelism and these multi

threading kind of a stuff

are fairly new to the Python.

Now I'm not saying these are only

designed in last couple of years, of

course they have been around for a

while and some of the frameworks

actually use them quite a lot under

the hood.

And also further down we are going

to see about the asyncio as well.

There are a lot of operations that

can be performed asynchronously

and we will talk on them as well.

Now some of the Python frameworks

use these async, operation like

insanely good and especially

frameworks like FastAPI, they

have pioneered the situation,

they work all of the things

asynchronously where it is

required, very beautifully.

But we'll have a discussion

on that one.

So let me take you onto the screen

and first we'll have a small

discussion on the parallelism and

concurrency and once we understand

them with the help of a diagram,

then we are going to go ahead and

write some code for both of them

as well.

But first let's have

a discussion on them.

So let me take you up

on the screen itself and yes, I do

have a diagram for concurrency

and parallelism here.

I will walk you through in that.

But my first of all,

the learning objective for this

whole video is simple.

I want you to make you

to understand the difference between

the concurrency and parallelism.

We are going to see some

of the real world scenarios of how

Python actually treats concurrency

and parallelism different

and where each of these things.

Further down we are going to talk

about the threading,

the multiprocessing and the async

programming in Python as well as.

So this is whole the thing that we

are going to work on with this.

First of all, let's talk about

them one by one and then we'll come

back onto the diagram itself.

First of all, let's talk

about concurrency.

Okay, what is concurrency?

We'll come back onto the diagram

as well, one by one.

But first of all, let's

see what concurrency is.

Concurrency simply means I want

to do multiple tasks at once.

Now, doing multiple tasks at once

doesn't make any sense, but, but it

happens in real world as well.

For example, maybe you are chatting

with a friend while making a tea.

Now, obviously you are not stopping

to make a tea, but whenever you

have to talk to your friends and

have to look up, you quickly look

at the glance and say some words

and then get back and start making

your tea.

And then again you do that so

quickly and switch between the

tasks so quickly that you also

don't realize that, okay, this

was the specific time which was

focused on talking to you, and

this was the time focused for

making the tea itself.

Just like I am doing this

concurrency, I teach you as well.

And I go ahead and write this.

So sometimes I go ahead

and work on this, that hey,

I'm writing something.

So I'm writing here.

So writing.

And I also explain you this stuff

and then, get back to writing.

So you see how fast that we

are able to switch this.

And computers are actually

much more faster than this.

Sometimes you, you don't need

parallel processing,

you just need concurrency.

Because CPU are expert

in switching the task.

They have this immense ability

to actually use every single

second and even milliseconds

and microseconds of the task

to do the computation.

And for this exact thing, you're

going to notice that concurrency is

something that can be utilized.

And this can be understood

by this diagram as well.

Notice here in the processing,

so notice here

the execution time is same.

And this is how

the concurrency works.

You do task for a certain

time, and once that time is gone,

maybe there is something

which requires some time.

Maybe there's some

calculation that's happening.

Maybe there is some file that you are

trying to read from the disk, or

maybe some database calls are there.

Now, during that time you

actually do some other task.

And this is how exactly your

operating system works.

By the time you are attaching some

of the peripherals, you are

attaching your keyboards or

anything like that, during that

time, other calculations keep on

happening, but you have limited

amount of cores.

Only that core is doing that task.

All right?

So I hope this makes it very

clear what the concurrency is.

And another concept that we have

just like the concurrency

is a parallelism.

Now parallelism is interesting.

Parallelism simply means

running multiple tasks

at the exact same time.

And Python actually uses multiple

cores CPUs to do these tasks.

And I will walk you through more

on detail as well into this one.

Now this you can assume

parallelism as two friends are

making two different T's.

That's parallelism.

So of course the friend doesn't

really affect other ones.

And here you can see in the diagram.

So these are different threads that

we have and these not threads.

But I would like to say

different cores would be good.

So this CPU has three cores

and each of the core is

doing different tasks.

And from the very first look it

looks like, hey, this seems better.

I should always use parallelism

because I, I have CPUs with multiple

cores and they can actually do

all the tasks in separate one.

But this is not like it, some

of the tasks either.

If, even if you're doing them

parallelly, you actually

cannot speed up the performance

onto like some extent.

Let me give you an example.

For example, this is your video.

Now this video needs to be processed.

Let's just say we are dividing it

into chugs or whatever we are doing.

Now in the concurrence you think

like, okay, if I just involve

one thread to do so, that probably

will take X amount of time.

So the X amount of time

will go just like that.

But if I actually go ahead and deploy

multiple of the processors, I

can actually do this task faster.

So maybe you decided that I will

chunk this video into different

segments just like this.

There we go.

And we can assign different

cores to the cpu.

So in that case, hey, parallel

processing looks good.

Each of the processor will

go ahead and process the video

frames separately on separate time.

And we can actually save some time.

Yes, in certain aspect, yes,

this is very useful, very good.

But what also you are not noticing

here that in the concurrency,

whatever the task, whenever

it is finished, you can actually

return the response there.

But in the parallelism, let's

just say this core who was

processing, or let's just say this

core who was processing

the whole thing, somehow got busy.

This guy is busy.

Rest of them are

performing really well.

They are doing the task at the exact

same speed that you are expecting.

But this blue guy is lazy.

And this happens quite a lot.

Maybe operating system has some

other important job to do.

They are not able

to release the core for it.

There are a lot

of things that happens.

So if this guy is lazy, you

cannot actually go ahead and return

the response because

the whole process is not done.

So although all of your other

workers were really fast, you

actually need to take the response

from all the workers, then have to

further add processing of

combining the result and you can

only combine the result once

everything is done and then only

you can go ahead and return.

So yes, there are pros, there

are cons for each of the task.

And until and unless somebody

discuss these tasks and discuss

these real world scenario, you

don't really understand and you

always think like parallelism is

much better of an option, but it

is not.

In real world.

In real world each of these have

their use cases, concurrency

have some of their use cases

as well as parallelism also

have their use cases as well.

All right, so this looks good.

Now further on, once you have

understood this part, let me

also go ahead and walk you through

that how this can actually

happen and what classes

and everything are being used.

So we'll take the concurrency

up here and this can go here

and there we go parallelism.

So how does the concurrency

and parallelism look like

in the world of Python?

Now surely this is not an exact

segregation, but some things

like this we'll be exploring

in the upcoming videos.

So whenever we are talking about

the concurrency, there is a module

threading and inside that you

actually go ahead and use thread.

Don't worry, I will walk you

through with the code file

as well just like always.

We have been doing this in this

series so far, so we will be working

with the threading thread

which is used for concurrency.

Another thing that is used quite

a lot for the concurrency is

Asyncio and we do have a chapter

on that dedicated which is coming up

just after this chapter.

So asyncio and threading, these

are the two things which are

closely associated for concurrency.

Now whenever you want to do

parallelism, in that case,

what the module that you have

to study is multiprocessing

and especially dot process.

Now multiprocessing has a lot of

things to use, but these are the

most common one that we'll be

using the now apart from that, we

will also be covering up one more

thing onto this one which is

concurrent futures dot and yes,

this is a long one.

I don't even remember.

I always kind of rely on the auto

suggestion that comes up.

But I'll walk you through

with this one as well.

Process, pool executor

and probably I'll mistype that.

But again, excuse me if I go

ahead and mistype this one.

So this process, pool executor, this

simply Says the exact same thing.

You have a pool of all the

processes that are doing the

task and once all the processes

have done the task, then we can

actually control and segregate

the result and then can return

it back.

So for parallelism, the two things

that you have to study is

multiprocessing process and another

one is concurrent, futures

and process poll executors.

Now we will also go ahead and study

about the coroutines

and stuff in the syncio, but that's

part of Asyncio.

I don't treat them as

a separate subject altogether.

So this is all what we have to study.

This part and this part.

So for the next two chapters we'll

be focusing on just this one.

All right, now how can we end

the video without actually

doing some of the practical

aspect and practical work?

So first of all, let's see a very

bare minimum example of concurrency

and the parallelism so that

at least we can go through.

All right, this is how

the code looks like.

I will not go too much in depth

in just the very first video.

In the upcoming videos we'll go

ahead and and explore each bit,

each part of it and you're going

to love this part as well.

So let me go ahead, I have this

thread concurrency challenge.

We have all of this going through

with the course and I'm happy

that in the udemy we have

covered so much of the content.

Now let's go ahead

and create this one.

I will call this one as 01 and let's

first use an example for threading.

Threading py I was thinking

of threading basics,

but threading is all okay.

Now how do we work?

First of all go ahead

and import threading.

Yes, threading is directly

available in Python.

No need to install anything else.

And for the fun let's

also include the time.

Now let's go ahead and define

a method that take orders.

So take orders.

What does it do by taking the orders?

Nothing much.

It just takes the order

and prints that how many orders it

is taking and going for that.

But I would like to do it

little bit extra thing.

In this method I will say

for I in range and let's just

say Our range is 1 to 4.

Always remember these

range are not inclusive.

And we will print a simple method.

Let's use a formatted string for this

and I will go ahead and say taking

because this is a take order.

So it says taking order for and then

we will use the ith value.

So you are taking the order

for first Guy.

But as soon as you take the order for

the first guy, then from the time

I go ahead and sleep this method.

Now why am I sleeping this method?

Because it can be a simulation that

hey, this operation takes some time.

Maybe we are extracting some of the

files from the disk, or maybe we

are making a database calls, or

maybe there is some complex

processing that's going on that

takes exactly one second and it

could be more as well.

But I think this is good enough.

Now let's go ahead and do

same kind of a thing for

brewing the chai as well.

Let's call this one as brewchai.

This is also another method

and that takes also some time.

So we'll just replicate exact

same thing for I in range

and let's use the same example Y

to differ there and print.

In fact, I can just go

ahead and copy this.

So move it up here.

And we are going to go ahead

and say brewing chai

for and whoever the guy is.

Now also we will go, actually I

can just go ahead and copy this.

There we go.

And in this case this takes more

time because it's brewing the chai.

It's a complex process.

So now we have two methods.

Take orders and brew chai.

And of course they work

synchronously hand in hand.

So in this case I want

to make two threads.

Now take this thread, in this case,

as kind of two waiters that are

doing the two separate tasks.

One is taking the order,

one is brewing the chai.

So we want to segregate this task

into two different people.

So two different people,

two different tasks.

So how do we create the threads?

Let's go ahead and learn

how to create threads.

It's actually super easy.

Now with this threading module that

we imported, we can just go ahead

and say, hey, this is the thread

that I want to create and you can

create as many threads as you

want.

Now what does this

thread is going to do?

By default, nothing.

And there's no point

of creating a thread like this.

A thread should have some target

that, okay, this thread will

go and execute some function

and will get us the result back.

So in this case what you have

to do is provide a target to it.

So the thread target

here is take orders.

So this will go ahead

and take the orders.

I will go ahead and call this,

this is my order thread.

So some of the tasks will

be done by like this.

And similarly we can go ahead

and say threading thread, I will

create another one who will have

another target to work on with.

So this is the target

and we're going to go ahead and call

this one as brew chai.

So one thread is responsible

for taking the orders.

Another thread is responsible

for brewing the chai.

Simple, super simple.

Told you I make the example super

easy so that you never forget that

I will call this one as brew thread.

There we go.

So super easy, nothing complex.

Now once you've created

the thread, doesn't mean you have

invoked them, doesn't mean

that you have started them.

They know their target, they

are just sitting up there.

But they don't work out

of the box like that.

You have to actually start them.

So it's super simple.

Python makes it super easy.

I can just tell my order thread that

you go ahead and start this, it

will go ahead and start its working.

Similarly I can go ahead

and start this brew thread.

Brew thread and I can say you

also go ahead and get started.

Super simple, nothing

complex in this one.

Now once they have started, as I

mentioned that can I go ahead

and just print my statement or give

you the result once the order

thread has done processing?

Of course not, because these are two

different threads who are working

on two different processes.

This is multi threading example.

I cannot give you the example or

the output result until the brew

thread also have finished.

So I have to wait for both

of them to finish.

Until then I cannot actually go

ahead and work on with this.

So in order to wait for it and again

notice this is an example just for

wait, wait for both to finish.

So how can we go ahead and do this?

Super simple.

Again order thread also has

this method that says join.

Now notice here the join says wait

until the thread terminates.

This blocks the calling thread until

the thread whose join method is

called and terminate either normally

or through an unhandled exception.

We will talk about then handled

exceptions and all these things.

So a thread can join

many times as well and all of this.

So this is basically an example of

join simply means hey, you

have finished your work and now

come back and report to me.

That's it.

And then once this is done

let's also go ahead and call

not the break brew thread.

And this also needs to join.

There we go, two threads

working independently.

Once this is all done, let's

also print a simple message that

simply goes ahead and says

all orders, orders taken and chai

served, not served, brewed

because we haven't served yet.

We could have another method

for that which has another thread

which is serving another

but this is a good example

to understand and I don't Think so.

It's very complex as well.

Let's go ahead and open this up.

I will open this as

an integrated terminal.

Looks nice.

Python is going to run

the only file that we have.

Notice here brew is taking

the order brewing chai.

So there we go.

So all of them are now

done and completed.

So I just want you to understand

and notice and pay a little

more attention on,

on how the output is coming in.

I think I should actually get

more of the time in this.

So I'll just go ahead and say

this is going to be two,

this is going to be three.

So we have more time for us

to actually discuss how

the output is coming in.

As soon as I started, the first

order is taken up,

but the brew is going with that.

Now notice here, order taking

is much more faster,

but the brewing is taking more time.

But also you will notice

everything is going in order.

It's not like hey, first guy

is running much more faster.

Although the sleep time of the first

guy is only 2 seconds and for this

guy it's actually much bigger one.

Of course it's not 2 second

exactly, but you get the idea.

Let's assume this is two seconds

and this is three second.

Again I'll not go into too

much of depth of that.

We have discussed the time

and everything right now.

We want to understand this.

Now notice here how does

the output look like?

I have taken this order.

My, my sleep time is actually less

and this guy takes more time.

So until, unless this

guy has processed.

So now the thread turn is this guy

and although these looks

very independent altogether

but notice here how synchronously

they are working on.

So this is all that I wanted

to explain you that how

the things are going on.

Now the key takeaway here is that

you have only one core which is

getting engaged in this one, but

you have multiple threads which,

which are switched very

frequently and they are

performing the task.

So you don't have multiple cores.

The multiprocessing is not going on.

This is multi threading and if

I just take you onto this,

this is multi threading.

So what we are doing is concurrency.

We have one single core which is

doing all the tasks, but we were

able to just get the things done.

Now the beauty about this is in case

you have some heavy duty operation,

you can actually perform that onto

a separate thread altogether and

you can just take the priorities

and everything on separate on this

one.

I'll not bore you onto this one too

much, but this is the very basic

and first example of it as we go

further, I will explain it more.

But I think now you have

tiny bit confidence that,

okay, it's not that hard.

The threading looks okay,

I can live with that.

Now let me also give you another

example of this which is going

to be multiprocessing and then

we can compare them better.

So let's go with this and I

will say this is processing.

Multiprocessing would be good.

Multiprocessing.

Py.

All right, so how does

the multiprocessing works?

As I mentioned this one, remember,

Multiprocessing process.

Yep, that's exactly.

So let's take this

from multiprocessing.

We are going to import process.

Good enough.

We are going to go ahead

and import the time and.

And let's also do the kind

of exact same example in this one

with a little bit of twist.

So we have a simple method that goes

ahead and simply say brewchai.

This takes a name of the chai

you give me and I will go

ahead and brew you that chai.

First of all, let's print

the statements and I will say

like this and name chai served.

And once you serve the chai, then

we go ahead and take the time

and sleep it for how much seconds?

3 seconds would be good enough

to discuss all of this.

And once this is all done, then we

print and we go ahead and say this.

Let's actually call this one as

start of chai brewing.

And we can have a copy of this,

this can go away and I

can say end of whatever the chive

that we are brewing.

All right, seems decent,

no problem there.

Now let's go ahead

and use the dunder.

It's been while we haven't

used these dunders, so

let's go ahead and use them.

And we can say dunder main.

And in this one let's

have a variable chai.

So you have a lot of chai makers.

Now notice here, the example that

we are trying to do is this one.

So we have multiple servers, multiple

cores will be engaged and they

can actually go ahead and keep

on serving you different Chai's.

So how do we work with that?

You have a simple array and the first

thing that we are going

to do is leave it as empty.

Remember we discussed this so

many times and here first

of all, I'll write the loop

for I range, whatever,

the range you want to pick up.

Let's just say three.

Good enough.

And now all I have to do is

how does this work?

So for each of the range I, we

will have process no suggestion.

Oh, because of the indentation error

process.

And we are going to go ahead

and say it requires two parameters.

The first one is target.

No suggestion.

But anyways we know the target exists

so this one will be Brew chai.

All right, we have the brucha.

Why is it having the issues?

We will figure them out and we

can have the args just like this.

And why are you having the issue

you shouldn't be having anyways?

Oh, my bad.

There we go.

It was just right in front of me.

I think now we can

have the suggestions.

Yes, now we can have the suggestions.

So for the args we are going to

go ahead and say a simple formatted

string where we are going

to pass the parameters as well.

Let's call this one as chime

and we'll just go ahead and give it

like this I plus one super simple,

super easy work like that.

And additionally

we'll pass on like that.

All right, so this is

not really that hard.

We are writing just a simple list

comprehension which goes from range

zero to three and we just

provide this argument chimeaker.

So wherever is your target

we are providing this name.

Here I am giving you extra name

as i1 because we just have

a simple range and this is going

to serve the chi name at set.

I can do better.

I will show you that.

But first of all let me go

ahead and get back this.

All right, seems decent.

Okay, what do we want to do now?

This is just a variable

with some processes

in its array that's linked.

First of all, start all process.

That's also I have to do.

And apart from this, what also I need

to do is wait for all to complete

because remember the diagram, I need

to actually work with all of them.

If one goes lazy, my result is

going to compromise there.

So how do we start all the process?

I can just go ahead and say for P in

chime this is my array simple one,

I can just go ahead and say P start.

So for each of the process

I'm calling this whole thing

as P and I just add a start

onto that and that's it.

It's a method.

There we go.

So I've started all the process

and now I have to wait

for each one of them to complete.

So for this also I can say for pin

chimekrs and then I can

just go ahead and say P join.

Yes, the same method works like that.

And once this is all done I can

just go ahead and get out

of this and I can say print

and this can say all chai served.

All right, now let's first see

the magic, what's going on with

this and then we'll probably improve

the namings a little bit.

So let's say Python

is going to run 02.

There we go.

So notice here all of them

got started of brewing the chai,

and all of them got started

with ending of the chai.

This is much faster,

of course, because a lot of cores

are being engaged this

time and we are waiting.

We are not actually going ahead

and printing the result as we go.

We have to wait for all the cores

to process this one.

Is it faster than the previous

example threading?

Yeah, because we are actually

waiting for two second.

But hey, different course.

And all of these threads

of the cores, or in this case we can

say processes, all of the processes

are reaching to the stakeholders

at the exact same time.

Now this two second delay,

they all have to wait.

But they all are like you have

three waiters in the restaurant

now and all of them are reaching

to the kitchen at the same time.

All of them has placed the order.

Once the order is ready, all three

of them pick the order or the tea

and serve it to the customer.

This is how

the multiprocessing works.

So notice here, here you have

all the three workers.

Here you have just one guy who is

kind of switching between the task

and that's the whole example.

Now I think it will be much more

easier for you to understand that,

okay, in the threading world we have

the thread, but the processor is

one, the core is actually one.

And that's why we actually, no

matter how many threads you actually

engage, it's going to finish

because it's switching the context.

But here, in this case,

multiprocessing, they're all going

through with one thing.

All right, so quite a good

example and we have worked

quite a lot on this one.

I would say let's call it

a day off just with this one.

Again, the future examples will

actually make things much more clear

than what we have done here.

This was just a basic example.

As we go further, you will

enjoy this multi threading

asyncio much more in this one.

That's it.

If you have enjoyed this, check out

the ratings section as well.

I expect that if all things are

going good, do rate us as well.

And if you have any

doubt, let me know.

And that's it.



Hey there everyone, and welcome

to the Python course on Udemy.

In this video we are going

to work on GIL or also known

as Global Interpreter Lock.

Now this is a very fun concept

and of course we're going

to write some code as well.

There are ways that, where you

see this lock in action

and also there are ways where you

can bypass this lock as well.

Of course, the bypassing of this

lock comes with its own

consequences, but rather

discussing about that first, let

me take you onto the screen and

I'll walk you through what this

whole thing is going on.

So in the world of Python, if you

go ahead and look onto this one.

So let's just say this is the basic

Python that we are going.

And by the way, we are learning all

the C Python that is classic Python.

The memory, management

is not thread safe.

And to avoid the race condition,

when two threads are trying

to access or modify the same,

object in the memory, then

the race condition appears.

And Python uses something known as

gil, which provides a simple mutex

so that no two threads can actually

change the memory at the same time.

I know that's a lot, but let me walk

you through the easy way of it.

This is your memory.

All right, great enough.

And in this memory this is,

some value and I can just go

ahead and say this value is 4.

Now you're using different threads.

Let's go ahead and call this

one as this is my thread

1 and this is my thread 2.

Rather better to call this one

as this is my thread one

and this is my thread two all.

Right, good enough.

This is thread two and this

one is going to be thread one.

Now both of these threads wants

to go and change the value

in the memory, just like that.

So who will be changing?

This guy wants to Change

this value as 5.

This guy wants to change

this value to 3.

Who should be doing the task

and who should be the final

source of the truth.

Now to avoid these kinds of complex

behavior, when you want to change

the same memory location or

same object in the memory, Python

uses something known as Mutex.

Mutex is nothing.

It's a mutually kind

of exclusive lock that we have.

It's a locking system.

Basically, once a thread reaches

to up whoever gets this Mutex lock,

the other guy cannot actually

go ahead and touch this memory.

Yeah, that's really simple

and that's what GIL does.

This Global Interpreter lock,

as soon as you touch this memory

by any thread, you get this mutex.

That means you have the full

control on this memory space.

Now, no Other thread can enter

this space, change the value.

Nothing like that can happen.

Once you're done with this, then

you go ahead and say that, all

right, my whole job, that whatever

I wanted to do is all done.

I will go ahead and remove

this Mutex now.

And other guy gets this mutex

and now he can go ahead and read

the value, remove the value,

whatever he wants to do.

This whole thing is super

interesting and important as well

because it actually helps us to

avoid certain scenarios where we

have the race condition and the

whole thing where two threads

wants to access the same memory

location and want to change them

at the same time.

This is known as race condition.

It's a very, very interesting thing.

Almost all of the databases do

have the race condition and there

are mechanism to avoid them.

A similar thing happens

in the Python.

So I think now it's good.

And by the way, if you want a real

world example for this, kind

of think of this as a chai counter.

No matter how many baristas

are around, only one order

can be processed

at the counter at the same time.

This is like the best

real world example.

Now should we go ahead

and write some code for the GIL

in action using threading?

Let's go ahead.

Okay, let's go ahead

and write this code.

That would be fun.

And this will help us to show

that although we have multiple

threads, but no speed and process

is going on to there.

So let's call this1 as 03.

I'll call this one as Gil Py.

Not just the Gil.

I think Gilthreading

Py would be a better name.

Okay, how do we work with that?

Super simple.

We go ahead and say give

me the threading,

give me the time basic.

We have done this.

And then let's go ahead and call

this one as Brew Chai.

Super simple, no big deal there.

We don't take any parameter,

anything inside that.

We simply print up a message

just like this and we simply say

inside this we have the threading

dot, whatever the current

thread that we have.

And also we can get the name

of this thread.

I'll show you how the name can

also be done, but it has a property

of naming this thread.

And this one says this one started

the brewing process with few dots.

Three dots is good.

All right.

Okay, once this is all done,

what do you want to do now?

I want to have a variable count.

There we go.

Super simple variable.

But a lot of operation needs

to be done on this count variable.

So what I can do is I

can Run a simple loop for

something in range.

And we have so many

of the big number here.

So let's just say we have.

This is a lot, this is

a big work and this is

actually a CPU bound work.

So going through this range obviously

going to take some amount of time.

For all of this, all I want

to do is clown plus equals one.

So I am changing

the values one by one.

But it's a really long value

and it's going to show us

that how things are going on.

Now once this is all done, now

we can go ahead and say, hey,

this guy finished the brewing.

All right, so this will help us

to understand that.

All right, if a thread goes into

this and want to do some operation

in the count, it takes some time.

Maybe it's an image processing

work, video processing,

it could be anything.

But this time it actually

takes some time.

Definitely my CPU is fast,

but not that fast to process this

in just a millisecond.

It will take some time.

All right, seems good enough.

Now let's go ahead

and create two threads.

In case you forgot, creating

the thread is super easy.

You go ahead and say threading

and I'll just go back here.

Threading thread.

There we go.

Created the thread,

it needs to have a target.

What target you have?

We have just one method

in this case which is brewchai.

And also alternatively we are going

to provide a name to this as well.

So name is going to be.

Let's call them baristas.

Barista, you don't have a name.

You are just Barista one and another

one you are Barista two.

All right, let's hold them

into a variable.

Let's call this one as thread

one and this one is

going to be thread two.

Thread two.

Super simple, no big deal.

Now once this is all done,

what do I have to do?

I have to track the time as well.

Or don't forget to join them as

well because just creating

the thread it, it doesn't work.

You have to start them

and then join them.

Join means wait for all

the things to complete.

So let's go ahead and say start.

How does it start?

Time.time time.

Time.

This time.

Time.

This will start the time.

I will say T1 start.

Not T1, thread one start.

Same goes for the thread two.

You also go ahead and get started.

Once you have started, I need

to wait for your finishing as well.

So I'll just go ahead and say join.

Same goes for thread two.

You also do all of the job

that you have to do.

And then we also need

to measure the end time as well.

So time dot time.

There we go.

And finally we can print the time.

This is a very classic

technique, doesn't work well,

but hey, it's fun.

Total time taken is going

to be end minus start.

And what we can do is get the 2F

so that it doesn't give us

the long value and seconds.

Seems good, fairly simple

program, but actually

shows us the GIL in action.

Let's go ahead and open this up

and say, hey Python, I want

to run the 03 Gil threading.

Notice here it says all the Barista

1 and Barista 2 they have started

but it's taking really a long time.

They took the time just.

And just because we have

the same variable that

is getting manipulated.

The Mutex came into the picture,

the GIL lock came into the picture

and said oh, I won't allow you.

Although you are a thread,

you are on its own.

But since you are actually trying

to access the same memory in the

memory, trying to access the

same object in the memory,

that's why I won't allow you to

do this and you will take your

own time.

So no matter where you run this,

no matter how many threads, you

actually execute this, because

they are not processing

concurrently or parallel, nothing

like that, they are doing the job

one by one.

But there is a way

where this can be a bottleneck

and you can bypass this.

Now again, bypassing comes with

its own risk, so be very careful.

But there is a way

of how we can bypass this.

Okay, I will go ahead and create

another one here.

This is going to be 04

and this one, let's just say

call this one as gil and this one

will be multiprocessing.

Py.

All right, so how does this one work?

This time we want to go

with the processing,

not the threads again.

Remember in case you forgot,

process threads.

So no threads and the process

so processing.

Whenever we go with

the multiprocessing, it's

actually parallelism.

And this one here, whenever we go

with the thread we are trying

to go with the concurrency.

I should have changed this.

But this is actually accurate.

This is not wrong.

This one is more accurate.

Anyways, so from multiprocessing we

are going to import the process good

enough, Import the time good enough.

Then we have crunch, number,

not like that, crunch number.

There we go.

And again, same thing.

We'll just go ahead and say

hey, we'll have the count

that is going to be zero.

I'll probably say this one as

print statement here as well.

Started the count process

with a few dots and this one remains

same for something in

range, which is really a long one.

So let's use one.

This is a pretty big one and all we

got to do is count plus equals one.

So we're incrementing it one by one.

This one needs to say that

ended, ended the count process.

Seems good.

All right, now first of all,

let's start the timing.

So start is going

to be time dot time.

Super simple.

Now let's create the processes.

We can start the time

after that as well.

But anyways doesn't

really matter much.

So first of all this process,

we can run a loop as

well to get the process.

But the whole whole point is

get the processes ready.

The target is simple, we have

the crunch number and yes, by

the way, do we have more parameters?

Of course we have the daemons,

groups, names, all of them.

Doesn't really matter

much in this case.

Name.

Should we give the name?

Let's actually give it a name.

Let's go ahead and find this out.

And I'll not do it.

Sometimes I get really overboard.

All right, so this is my process one.

I'll call this one as P1

for short and I will call

this one as P2 for short.

P1 needs to start.

So P1 start, you go

ahead and get started.

And P2 also needs to get started.

So P2 you also get started.

Need some room.

Once this is all done, let's wait

for finishing of the P1

and let's go ahead and also wait

for P2 to finish the job.

Let's calculate the end as well.

This is super simple.

We can say time.time and now

after that we will print this.

So we'll go ahead and say

print a formatted string where say

total time with multi

processing is and we can calculate

the same end minus start.

And this one is going

to get two F seconds.

All right, so this is all

that we wanted to write.

Now here's the very

interesting thing.

Now notice here, compare this code.

Don't worry, I will

run the code as well.

But if you look at this,

this code works absolutely fine.

We have the protection mechanism

and everything is going on.

But once you see this code, this is

a very interesting piece of code.

Now if you have noticed, sometimes

I do write this main method,

sometimes I doesn't write them.

Notice here we are

writing this main method.

Here in the thread we were okay

for not writing this main method.

Now this is where for the first

time you see that what happens

when you write these main methods

and what happens when you

don't write these main methods.

Now, in case you are using

threading, multi threading,

then it's totally fine.

Let me go ahead and close

the others as well.

Because threads are actually

designed in such a way that they

know their entry point, they

don't do any spawning of the new

process and everything.

But once you're using multiprocesses,

your process sometimes doesn't

know that much of the information

which your threads knows.

So in this case, what you're going

to see is a whole big error.

First of all, let's go ahead

and see that error errors

actually teaches you a lot.

All right, so let me go ahead

and open this up into

integrated terminal again

and let's say, hey Python, I want

to run 04 and there we go.

And here it is.

And if you look closely into this

error, it error says an attempt

has been made to start a new process

before the current process

has finished its bootstrap.

Bootstrapping is a starting

phase of your application.

Your threads or your processes

rather doesn't know that whether

application is already running.

And it's basically you have no way

of protecting your entry point

of your application in that case.

Whenever you see these kinds of

errors or anything error that says

spawn fork or anything, also always

look for this notice here.

This doesn't have this exact line

and this is the free support that

means a line can be omitted if

the program is not getting frozen.

Basically what's saying

that, hey, I don't know where

to start your program.

What is the entry point of this?

So what we can do is we can

take all of this code from here

to here, cut this out and can

say, I will just go ahead and say

name equals dunder main.

There we go.

And we can just go ahead and give

them a small indentation.

And now, at least one

problem has been resolved.

All right, seems good.

Now let's go ahead and see more

onto this what happens.

All right, so run this again.

And there we go.

Started the count process.

Started the count process.

This one takes 2.8 seconds.

But on the other hand, if I go

ahead and run the other guy,

which is in the 03 and the same

code, same processes and everything.

This one takes more time.

Exactly.

Same things.

This one is taking five

seconds almost twice as time.

So one thing is, we are sure that

if we have more workers, more

threads or more process,

they actually reduce down our work.

And especially in the case when

we have multiple processes because

multiple waiters are there.

They help us in reducing the time.

But again this can be

dangerous because you are

overriding your mutex.

You are overriding the security

feature so be very careful for that.

A lot of people use this as well but

you need to know that when you have

the GIL implemented good for you

and the lock is good one for you

and when you can actually avoid and

bypass and actually speed up the

process.

Again there are pros and cons.

There is no one shot, one

silver bullet that fixes everything

but hope this global

interpreter lock video now

helps you to understand.

All right I know it and I'm going

to use them precautionary

and again hope you are enjoying

the error part as well.

I love to show the errors

because that is one thing

which teaches us the best.

That is it for this video.


All right, welcome to the video

in the Python course on Udemy about

threading or threads in general.

So so far we have seen the basic

overview of what is gil,

what are threads and process.

But this video is a deep

dive into the threads.

We will learn about the lock state

and everything that you probably

need to know about the threads.

It's not really a long topic,

it's a implementation topic.

Once you see the implementation

in the real world, whenever

you'll be working in Python, then

it starts start to make sense.

Otherwise it's just like it's a loop.

What I'm going to do of doing

the task like hundred times.

But when you see the real

implementation like you get

the value from database, you process

that value, something like that,

then it makes much more sense.

Now before going further into

the thread, in the code part itself,

I want you to see two diagrams.

Although these diagrams are like more

of a foundation of operating system

as a subject in computer science,

but maybe you haven't seen it much.

Still I want to walk

you through with this.

So if you just look at the thread

versus process diagram, this is

what you need to understand that

how the thread and process works.

So I'll probably not zoom that much.

So here the thread versus

process versus thread.

First of all you can see that this

one here is a single thread and not

really that great of a diagram,

but this one actually makes sense.

So whenever you have a program

inside the program, you have a lot

of instructions and program

can actually work with multiple

processes and each process

can be divided into the threads.

That's the basic of it.

And, and here is a diagram again,

nice one, process versus thread.

You can have multiple

of the threads and this is the whole

process, goes like that.

But again the topic of thread

versus process is more of like

an operating system, topic.

So once you're getting your

foundation of operating system

solid, try to study it there.

I won't be covering it too much.

This shouldn't be a part

of this course.

Like hey, the difference

between the thread and process.

If you want to see this, this diagram

actually makes much more sense here.

I think this is the, this is

a single threaded process, this

is a multi threaded process.

So process remains same, but you

can actually divide the things

into each of the process.

And remember each process gets

its own counter, the stacks

and the whole code data.

But data is actually shared

in the thread case the process.

Since the CPU is completely

different, it's a whole

different process as well.

So again you'll find much more of

these Diagrams and the whole things,

they actually work like this.

So this is a process.

The process can have

multiple of the thread.

Each.

Each process has its own memory.

That's probably the foundation of it.

And again, once you're studying,

the operating system,

then it actually makes much

more sense anyways,

so this is what we'll be doing.

Now the topic that we want to study

in this case are just the threads.

Some of the code will feel like,

hey, we are repeating this stuff.

But it's necessary actually

to understand the thread part.

So rather than going, onto

the diagram itself, I would like to

take you onto the code part itself.

We'll be creating multiple

of the code files and I

want your full attention

onto the code part as well.

So let me just remove myself

and get onto the code again.

As I mentioned, some of the code

will look like kind

of repetition, but it's necessary.

Let's create a new file and this

one we are going to call 5th so 05.

And I'm going to call this

one as thread 1 py because

we'll be creating multiple

of the thread files.

So starting will always be similar.

You have the threading.

Let's go ahead and also import

time to do some fun stuff.

Not really necessary.

Let's just say the first method

is just for boiling the milk.

You boil the milk, you sleep

for two seconds, and then you

say, hey, the milk is boiled.

So let's call the method as boil,

underscore milk goes like this.

We have a simple print method that

goes ahead and says boiling milk,

super easy with few dots, of course.

Then you go ahead and sleep this one.

So time, dot sleep.

And let's just say this one

sleeps for two seconds.

Not exactly two seconds.

There's a whole mystery about it.

But that's okay.

That's for another day.

This one is milk boiled.

So I'll say milk boiled.

And let's have one more which is,

toasting the bun.

So let's call this one as toast bun.

And again the process is

almost exactly same.

We go ahead and print out a simple

method that says toasting

bun with of course a few dots.

And then we go ahead

and get this one here.

We sleep again for three seconds

and this time we duplicate

this and we say bun Toasting.

Done.

Done with bun.

Come on.

My keyboard seems to be off.

Done with bun.

Toast.

All right, good enough.

How do I go ahead and do

all this process?

Like if I go ahead and execute this

just by default, Like I go ahead

and say, hey, boil the milk.

And I go ahead and say

toast, the bun.

So this is just a main thread.

You have just one thread, one core

process that's going on and it's

going to go ahead and execute that.

But sometimes you want to control

that, that, hey, I will have one

of the thread which will

do one task, another thread

which will be doing the task.

Although you don't need

for this kind of a basic stuff.

But if you want to control

the threads that, hey, I have

some of the process, I want some

dedicated resource

for it and that's totally fine.

In some of the cases it is required.

In that case, let's go

ahead and work like this.

So I have a T1 of a thread

which is going to get

started by the threading.

Remember we have the threading

and for that we start a thread

and we go ahead and say target

is going to be this one.

One thread will be busy for boiling

the milk, another thread will

be busy for toasting the bun.

So we have two waiters,

kind of, and each of them

doing their own task.

But just by doing this we know

that the task is not yet done.

So for this we have

to start this thread manually.

Similarly, we have

to start this thread as well.

But we cannot just start them, we

need to wait for their execution

to be completed because they might

be doing a lot of tasks that

might be CPU intensive and stuff.

So T1 is completed and then we have

T2 also we want to wait for it.

So T2 is also completed and we can

go ahead and calculate the end time

just like we have done in this.

So time, dot time.

This gives me end time.

And finally I can just go

ahead and print the values

and simply say not like that.

There we go, breakfast is ready in

now calculate the time so end

minus start and we can go ahead

and say start, get set, to F so

that only two digits are there

seconds.

Seems simple, Very reasonable

program, nothing much of a big deal.

I can run this simply by saying

Python, you run the 05 program

and there we go, boiling the milk,

toasting the bun, milk is boiled.

And notice here, done with the toast.

Took more time because hey,

but we didn't executed that.

Hey, whole breakfast is ready

until the whole bun is ready.

So this is how you wait for it

and stuff like that.

Now surely I would like to create

one more file to give you more

of the practice on this.

We can actually manipulate

this one as well.

But I want you to see and get

more practice on this.

So let's create a new file.

It Will be very simple

but more practice.

Let's call this one as thread two.

All right, so how do we start?

Super simple Again, go ahead

and run with the threading.

We will be having some fun

with the time as well.

Get this, this time we

have just one method.

Let's call this one as preparechie

and somebody provides me the type

of chai that we have to prepare.

And we cannot actually use the type.

So let's use the type underscore

and we'll also have the wait time.

Fair enough.

Now in this first of all we want

to have a simple print statement

that says whatever the type

of chai you are working on.

So type and then we can say

chai brewing with a few dots.

Of course, let's go ahead and sleep.

So time, dot sleep and whatever

the wait time you ask me, I'll

just go ahead and sleep at that

time and I can duplicate this

and I can say the same chai

instead of brewing is ready when

it's ready.

It doesn't need three dot

personal reference.

All right, now let's go

ahead and create two threads

for each one of them.

Let's call T1 as the first thread.

How do we create the threads?

Hope you remember threading thread.

And this time

we will give the target.

Obviously the target is just one.

We have just one method to work on,

but we can actually go ahead

and provide the args as well.

So these are the arguments.

These argument lands up within

the function definition itself.

So in the args that I have is

it always takes the tuple.

The first one is masala

and this one will be prepared

in let's just say two second.

Let me go ahead and remove this.

And similarly we can have another T,

my favorite one which is ginger.

And this one takes more

time, three seconds.

And I will go ahead

and call this1 as T2.

Super simple.

Now the process is exactly

same T1 dot start.

You also have to start T2.

There we go, T2 starts.

And once the T2 starts we have

to wait for everybody to process.

So T1 join.

This simply join means join

me back once you are done.

So join just like that.

And after that we can

just work on with this.

Now since this is the thread, I

don't need to work too much on

that or need to worry about too

many of the things of locks and

everything or even don't have to

worry about the main method

itself because it's a one process

in itself.

And in the process there

could be a multiple thread.

So we Are basically what we are doing

in the diagram perspective.

This is our whole process and inside

this process we are controlling

the multiple threads just like this.

While on the other hand, if

you're working on the process,

I'll walk you through

in the next video itself.

But right now let's just keep it

in the thread itself.

This is the whole process and we

can call this one as main.

So this is your main going

on and inside the main you are

having multiple of the threads.

You are controlling all

of the threads, how much they work

on with that and everything.

But the only thing you have

to remember it's

one core, Only one core.

Or you can rather say one cpu.

That would also be good.

One cpu.

Yeah, seems good.

So there we go.

Let's go ahead and run this part

as well to see what's happening.

So Python, go ahead and run me 06.

There we go.

So this time the masala

chai is brewing.

And the masala, chai ginger

chai, all are being ready.

The important point here to remember

is how do we pass the arguments?

It's actually a tuple and, and as

many arguments you want

to pass on to the target, you can

just go ahead and say args

and pass it just like that.

Now let's also go ahead and work on

when the threading is not effective.

Yeah, you might be thinking,

hey, it's always good.

No, it's not that much good.

Always.

Sometimes it doesn't work well.

So let me show you one

interesting website.

So this is the website httpbin.org

notice here there is an image.

We have the PNG image,

we have the jpg image as well.

So they have different images.

Jpgp and gsvg.

I want to go ahead and download

this whole image.

All right, seems a good exercise.

We have done these kinds of

exercise in the past as well, many

in the projects.

So let's call this one as 07

and this one is thread download.

All right, so in case to jog

your memory that how do we go

ahead and download an image?

There are a lot of ways,

but one thing that we can do

easily by the request.

So let's go ahead and let's

assign different threads

to download the different image.

And this might give a sense

that, all right, we have different

threads, so they might be

downloading them in parallel.

But that's where you're wrong.

That's exactly where you need to

check out the diagram that we have.

If you think that three images will

be downloaded separately, remember

concurrency versus parallelism.

And this is one of the most

beautiful example of it.

Let's call this one as threading.

And we need requests, which is

by default available.

Hopefully it is.

Request is not accessible.

We need to install this one.

So probably I need to have

the virtual environment in this one

anyways we can have it, no big deal.

So this one is.

Yep.

So we can say hey Python,

go ahead and give me a module venv

and we can say venv and should be

having the virtual environment now.

And now I can go ahead and say

source, go to venv

Inside that we have Bin activate.

There we go.

We have this one.

We don't have requests, so we

go ahead and say first of all PIP

install and this one is going

to get upgrade of the pip.

So that should be just a second.

All done.

Now we can say PIP install requests.

So there we go.

Request comes up and there we go.

Ignore the squiggly line

because we know that we have

installed it properly.

I don't want to set up a separate

environment variable and stuff

like that, but you get the idea.

So import time seems good.

Let's create a method

which goes ahead and download

the stuff in this.

You just provide me the URL and I'll

go ahead and download this.

First of all print up a simple method

that says starting download from

and let's go ahead and grab the URL.

Seems decent.

Now using the request, let's send

a simple get request onto that URL.

Whatever comes to us, we'll go ahead

and hold this as a response fairly.

And we are going to go ahead

and print this simple.

There we go.

Nope, there we go.

All right.

And we can go ahead and say finished

downloading from whatever

is the URL and we can actually

find the size of it as well that

how much big the file is.

So for the size I can go

ahead and say I want to find

the length of something.

What something in the response we

have something known as content.

There we go.

It will give us the size.

The only problem is it actually

comes up in the bytes.

But we are not here

to convert them all of that.

Now let's go ahead

and define a URLs array.

There we go.

Why an array?

Because we have multiple of them.

This one is jpeg, we have one in png.

They support a lot of formats.

Svg.

There we go.

All right, so

preparation is all good.

Seems okay.

Now next up is.

Let's start this time dot time.

So start timer is ready.

Then we have this threads

A simple array, we will

have a lot of threads.

Now let's go ahead and loop

through the URLs and for each URL

we can go ahead and fire

up a thread for each one of them.

So For URL in URLs we can

create a thread just like this

threading dot thread.

What is the target that you have?

You have a simple target of

download and the args that you have

to carry is going to be URL

and make sure you put up a comma

as well because it's a tuple.

And then we can say T start

so it starts the thread.

And then we can go ahead and say

hey threads, the array that

we have, we are going

to go ahead and place it there.

Append just like that.

And we will append the thread.

Sounds good.

So we have an array of threads

which keeps on appending

this for each of the URL.

Very fair, very basic.

Now for the thread in threads

we can go ahead and join them.

So once you are all done,

join me back up here.

And once you are done with

this, let's also calculate

the end time which is start.

I was calculating the whole

time, but I should be

doing time, dot time.

Now I have a start time and end time.

I can just print this.

So print and we can say all

downloads done in whatever the time.

So end minus start.

This is going to be 2F seconds.

All right.

Now notice here, this is

an IO bound operation.

Threads can shine while

one waits for the data.

Another one can start fetching.

So it's really interesting,

whole thing as well.

Let's go ahead and run this

first and then we are going

to talk about this,

otherwise it will make no sense.

So I can say hey Python,

go ahead and run 07.

There we go.

So notice here it starts there but it

all finishes at the same time.

It still takes 1.5 seconds

to finish this.

Now let me walk you through

what just happened and how

we have optimized this.

First of all need to understand

some of the basics.

All right, we can actually

go ahead and use this.

Now notice here, this is

where the threads

actually can work on with.

So notice here, this is

a memory which you're trying to

change with the thread.

This is the place where

thread are not effective.

Yep, this is the process or the place

where they are not effective.

Because simple reason, if you're

trying to do any CPU intensive task

like image processing or large math

computation with the threads,

you won't get the speed benefit.

The whole reason is mutex and rather

saying accurately it's a GIL

which doesn't do the work.

But where really the use case

of the threads actually shines

are something known as

in this case IO operations.

So IO any IO bound operations,

threads actually shine.

Now IO operation, what

are these IO operations?

IO operations are of variety of type.

One of the most common one is

disk read and write.

Disk read write.

Another one that can also be

helpful is web requests.

So this is the place web request.

This is the place where all

of the threads actually shine.

You want to really use all the I

O bound operation because no

computation is being done.

When computation is being done,

that's only when you want

to write into the memory.

But in this case

a simple thread reaches out.

So this is your thread box and you

have multiple of the threads.

In this case we created

three threads obviously.

So each of the thread can actually

go ahead and make a web request.

So let's just say this

is our web server.

So each of the thread can

go and make a web request.

And by the time this thread was

responded because somebody was

giving it a response data as an

image, other thread also can go

ahead and make a request here and

other thread also can go ahead and

make a request.

And since they will be writing

into a separate memory location,

whatever the data comes back

from the server, we can go ahead

and write it at some places and

they could be all separate three

places.

So in this case

technically we have speed it up.

So notice Here we have three

different threads based on the URLs.

Each thread was busy

in getting the data from its

whole different thing.

There was no memory sharing.

And technically we have

improved this code.

And again the improvement is

not that visual because

the images are very short.

But hey, we are here

to understand the concept.

So this is a good code.

But you have to be very cautious.

Again, if you are writing with

the same file name or you're doing

something similar to that, make sure

you are onto the caution side of it.

Now again, this code was not

to make sure that the files

actually get downloaded or saved

into the binary format.

No, I was only interested in that.

Hey, I was busy in writing or

getting the response which

has this much of the data.

That is my goal.

So in case you see that hey,

the images didn't got downloaded.

We have worked on so many of

the projects in the utility section

where we have downloaded the files,

where we have downloaded the JSON

data CSV, we have done all of that.

So I don't expect them to do

these things again here.

All of my goal is to make sure

that you understand these things.

All right.

Quite a lot.

One last thing that I want to work

on with the threads is the lock.

So let me also walk

you through with that.

All right, so let's create a new one.

This one is going

to be 08/thread lock.

So there is a concept known as

this is optional concept.

It's a using of a lock

to handle the shared state.

What do I mean by that?

Let's go ahead and first

handle the threading.

Let's just say we have

a counter variable which

has initial value of 0.

We can also go ahead and use

a lock in this case.

How do we get the lock?

The threading actually gives

you the lock that you can use.

Lock.

There we go.

Oh, it's capital.

Forgot that.

And then let's just say we have

a method which is increment

basic method and all it does is

change the value of the counter.

In case you remember we studied

that if you want to address

this, first of all you have

to say global counter.

This is the counter I want

to change and use the same thing

for something in range.

And let's not use that

big of a number.

But I will say 100,000.

100,000 looks good.

Fairly decent number.

And now what we can do is we can

just like we open the file, we

can say with lock what it does,

it actually locks that particular

memory location for you.

So in this case, hey, I'm doing

some operations on the counter.

I'm saying plus equals to one.

Now, no matter the thread

you go ahead and create,

you have safely designed a method

which is thread safe.

Yeah, really nice.

So let's go ahead and create

all the threads just like this.

So this is going to be

a comprehension again super simple

for something in range.

And let's just say we want

to have 10 of them.

So we will be creating 10

of the threads.

Super simple.

We can use threading thread.

And where this thread will

go, it will have a target.

The target is increment.

Fairly decent.

Let me move that looks good.

And then we can do is

write a comprehension again

to just work with that because we

have too many threads 10.

So comprehension makes

day lifesaver here.

So what we can do is again for T in

all the threads that we have.

What do we want to do?

We want to say T

start just like that.

It's actually super easy.

Now we have to wait

for the join as well.

So we can just do exactly same.

And I have to say join.

There we go.

How beautiful the code is sometime

in Python once I'm done

with this, I'll simply go ahead

and print this and there we go.

It will say final counter

and the counter is going to go ahead

and say the value of counter.

Forgot the F counter.

There we go.

Super easy.

But now our method is aware

that there could be a Python

thread which might come to us.

So I am making sure that hey thread

do whatever they want to do.

But my method is actually safely

designed so that multiple threads

can access this and this memory.

I'm making sure that this

memory is actually kind

of a safe from the threads itself.

All right, let's go

ahead and run this.

There we go.

Clean this and this.

Time we want to run python.

This one is 08threadlock.

There we go.

So notice here this was faster

but again none of our

thread actually came in between or

gave the problem.

It's much more faster.

So lock.

So using a lock, ensure

only one thread modifies

the shared data at a time.

Without the lock you may get

incorrect results due

to the race condition.

And again there is no guarantee

that I will be able to show you this

result of the data, but I

want to still show you that.

Okay, so let's just say we

don't lock it and we still

want to work with that.

So I'll just go ahead

and comment this out.

Again it's a very difficult thing

to show because Python has its own

way of improving the things.

So not sure whether I will be able to

show a demo of it or not.

But this time we are not doing

anything inside the lock.

We just want to work with that.

Let's see what's the data

and what's the result of this one.

And There we go.

As I told you, sometimes it's

not that easy to show because

Python has its own safety nets

and this is just one CPU example.

My machine is already very

rock solid and all of that.

But again, compared to this code

versus this code, I would any

day prefer this code which

because I'm shorting, I'm

making sure that hey, I know

that the threads are going to

come into the picture and we

will work like that.

Hopefully.

That was pretty good.

And that is all, that is all you need

to learn about the threads.

This includes the threads,

the locks, where threads actually

shines, where they don't shine.

And that's it.

I'll revert this code here

because it doesn't make sense.

There we go.

We are using a lock and we

tried using without lock as

well the counter, but didn't

saw much of the result.

And that is why, I want to say that

sometimes it fools you so easily.

Don't get fooled in that,

having these kinds of code is better

only and only if you know

that threads are going to come

and manipulate these things.

So give them a global lock.

And anybody who wants to manipulate

this, pass this communication

to your team that hey, you have

to use lock to change this

variable so that we don't see

the race conditions again.

These are good practices

of the code, very advanced topics.

That is it for this one.


Hey there everyone.

I expect that now all of your

confusion regarding the threads are

all done and we have spent a really

good amount of time on them.

Now I want to spend a bit amount

of time on processes as well.

Multiprocessing or multiprocesses

is also a fairly complex subject

and one of the major issue

with the process is each

process gets its own memory.

Threads actually can share

the memory part because they are all

in one process itself.

But once you have multiple processes

that means there is no sharing

of the knowledge, or basically

the sharing of the memory.

So for these concepts a concept

known as queue is implemented.

Queue is actually a very

complex concept and it's all

together and we use them in web

development all the time.

But if you're using or happen to use

processes, then you should also

focus a little bit on the queue as

well and we'll cover that as well.

First of all, we'll write not so

efficient code using the processes.

Then we will write the efficient

code using processes and pardon me,

we will write the inefficient code

using the threads where thread

doesn't really shine and then we

will convert that same code using

the processes and then we'll work

on the queue.

And that's all you have to learn

about the processes, multiprocesses.

Let me share the screen with

you and go with that part.

Fairly easy, nothing to be worried.

We'll write them one

by one each of the process.

All right, so let's go ahead

and create a new file.

This is going to be 09.

So let's go for 09.

This one is going to be

process one py.

It's not really process

code, but still I'm keeping it

in the name of the process because

I want to show you that what

happens when things doesn't really

work well in that case.

All right, so this is not

going to be a process code,

but I want to show you.

So we have the threading.

We have seen this.

We also have the time.

We have seen that part as well.

And I'll quickly go ahead and define

some of the CPU bound work.

Let's call this one as CPU heavy.

Once you have the CPU heavy.

CPU heavy looks good.

CPU heavy.

First of all, let's print a basic

statement just like this and it says

crunching some numbers.

That's where you majorly

use the CPU bound task.

And it should be

crunching looks good.

First of all, let's have

a simple variable.

Call this as total,

which starts at zero.

Then you Go ahead and say

for I in range.

And we'll not.

Let's go with the range

quite heavy one.

So we'll go with the 10.

That's already a big number

altogether but that's fine.

We need to see that where

it doesn't shine plus equals

one Good here, not one.

Actually I would make it efficient.

And then it's all done.

It's a fairly

complex process of this.

Let's go ahead and use it.

Done.

And nope, cut this, Move it here.

There we go.

Now let's go ahead and create

a start time as well.

So time dot start,

not start time time.

This will give me the time.

Let's start the threads.

So let's use the comprehension

for the threads.

I will say for something in.

Not something like that

for something in range.

And we'll go with the two.

The only thing we need

to do is create the threads.

So we'll go ahead and say

threading dot thread.

And we know this, we have

to provide the target

in this case which is CPU heavy.

Let's store the whole result

into a threads variable.

So all of our threads, we have

seen this many times now.

So threads are there and we need to

write two more comprehension so that

we can start them and join them.

So we can say t start.

This is going to start

the thread and we can say

for thread in threads.

There we go.

And similarly we can also

go ahead and say this

will be join super easy.

And once everything is done

we can just go ahead and print it

just like that.

And we can say with the formatted

string the time taken is

going to be time dot time.

We haven't calculated the end

time so I'll calculate it

on the go itself and then I can just

go ahead and have a start time.

And once this is all done we

can just go ahead and say dot

to f and and seconds.

All right, fair.

Good enough.

So very simple, very basic.

But this is not a great or ideal

place where you might want

to run this code because

there is no efficiency in this.

So if I go ahead and say

Python, run this and it's going

to crunch the number.

It did it really, really fast and it

expected it to did it that fast.

Can we go ahead

and increase the number?

Probably nine.

That's a lot.

But I want to see more big number

and all right, probably too much.

That's a lot of processing now

just by changing it to the nine.

And this probably will give

us a lot of idea that hey,

this code can be improved.

Oh shouldn't have done

this much of the stuff.

Okay, I'll hit a control C

because it's actually too big.

I'll keep myself under control.

Let's go.

Only because each number

in this code is actually

getting a lot of numbers.

Yeah, I think this

one is also too much.

Let's keep the example same

for 10 to the power 7.

It's already a big number.

I don't know how it was able

to crunch it this fast.

All right, almost one second.

Can we do it faster?

Let's go ahead and copy this whole

code and move it onto a new file

and call this one as 10 and we'll

call this one as process 2 py.

Let's paste it as it is.

Now what are the changes

we have to do?

First of all, this is not

going to be a thread.

This is going to be a process.

So from multiprocessing we

have to import process.

Good enough.

Time will remain as it is.

The CPU task will remain as it is.

We don't want to change it.

The start time will remain as it is.

But this time instead of

getting the threads,

we need to get the processes.

Processes and the threading

is not going to work

or there is no threading thread.

We just have the process.

So there we go.

Process.

We need to give the target

this range remains exactly

same We need to join them.

So calling this as processes.

Processes.

There we go.

So now you have seen that how we

can convert a thread into a process

and this will remain as it is.

Let's see what efficiency

we are able to do this.

Now let's go ahead and run this

and this time it's going to be 10.

There we go.

Oops, my bad.

Because we didn't added it

whole code into the main.

We have already seen

this part as well.

Let's go ahead and cut this out

and we can just go ahead and say if

dunder name equals to main dunder.

There we go.

Process that.

Get the indentation ready.

And I'm really happy that you are

not afraid of this now that you

know exactly what went wrong.

And that's why I show you the error.

So that when you see the error,

it's actually okay,

I know how to fix that.

So I run this.

And notice here this was 0.35

second considerably good.

Now here's the interesting part.

Can I go ahead and do

eight on this one?

Let's go ahead and work on

with this crunching the number.

This is already fairly a big

number but hey, we were able

to do in the three seconds.

That's good.

Fingers crossed.

I don't know how powerful

the machine that I'm working on is.

But hey, why to shy away from this?

Let's see how much of the number

crunching can you do

with this one previously if you know

we had to wait so much

of the long that we just removed it.

I'm not sure how fast it's going

to be because it's actually

a very very big number.

10 to the power of 9 is

actually really big but I'm very

sure that it's going to be faster

than the threads itself.

I think we got a little bit greedy

there by getting this number.

But hey, the result

in 10 to the power 8 is

significantly visible.

There we go.

Took 30 seconds but hey, 30

seconds is much faster.

It actually got me the result.

So yeah, pretty big number.

We have crunched that.

All right, now one thing also I

would like to discuss on this.

All right, this part is all good.

Now let's create a new file.

Call this one as 11 and this one is

processq.py now one of the common

thing that you should know

that in any of the processes

the communication is a problem.

Memory is not shared.

So you need to use something

which can actually responsible

for sharing the memory.

It can be queues, it can be pipes.

There are a lot of ways of doing

the things and what I really like

about it is once you go ahead and

explore this multiprocessing

package, if you go ahead and see

import there are so many things

up here.

There are processes, there are

arrays, barriers, conditions.

So many things to work

on with one is process.

So we actually import that.

But if you look at this we

still have so many of them.

One of them is actually Q.

So yes, multiprocessing knows

this problem that hey, whatever

you are doing, probably you don't

have a queue infrastructure.

So once I go ahead and even

defining before the method or

anything we actually go

ahead and generate the queue.

How do we do that?

Just simple, that's it.

And hold this as a variable.

If you have studied any data

structure or algorithm.

Yeah it's exactly the same queue.

It's like a array but on steroids.

So let's define a preparechai

as a method it doesn't

take any parameter except the queue.

Most of these kinds of parallel work

you're going to see that somebody

goes ahead and passes us the queue.

There we go.

So this Queue is being passed

on and don't worry, I'll fix that.

All of these things as well,

don't you worry on that part.

So this queue that you have passed on

is going to have a lot of methods.

By the way, we can go ahead

and study this queue as well.

It has the initialization,

then we have get the state, you can

get this but you have the put

as well to add any value to it.

There is a reset as well.

There is a get as well if you want to

get what all the values it's storing

you can find the size empty, full.

It's a really full blown data

structure that they have prepared

for you and you just have

to got to use this one.

We'll keep it simple, we'll just

use the put and you can put

anything into the queue and in

any format you want to use.

Dictionaries, arrays, almost all

of them are supported.

I will just go ahead and say

Masala chai is ready.

Very basic example.

Now let's go ahead and get the

process ready which targets one

method only which is

preparechai and in the args we

go ahead and pass on just the

one which is Q for us and again

it's a tuple.

So go ahead and put up a comma

and let's call this

one as P for short.

P is going to go ahead and start this

and P is going to go ahead

and join this and that's it.

And I can just go ahead and print.

Oops, I can go ahead and.

Yeah, I know how to type print

and what I want to show

you is that we have now some data

inside the queue.

So any other process can go ahead

and come and can pick the data

from the queue itself, process

it more, probably put it back

into the queue, whatever is there.

Now our method doesn't just return

the value, it puts the value

or the data inside the queue

and that's the most important part.

So let's go ahead and run this.

This one is 11.

There we go.

Oops, my bad.

Should have done it more carefully.

Copy this and we can actually go

ahead and work just like that.

There we go.

Select all of this.

There we go, should be good

and there we go.

If I run this.

There we go.

Masala chai is ready.

The reason, I hope you

understand the impact that

we have created here.

The impact is the most

important thing.

The impact is that, that now our

method has put something inside a

new data structure which is Q and

this as long as you pass on into

the argument this Whole data

structure is being passed on to

one method, to one process or to

100 process.

All of them will get the access.

Now we have other shared

state, as well.

Like we have a value, we have

an array, and all of them

actually comes from here.

So if you go ahead and look

onto this, we have this something

known as value here as well.

And how do you use

a value here as well?

It's a pretty simple process

to work on with.

I'll just show you

as a brief example.

Let's just say you want

to create a counter.

So in this case I can go ahead

and create a counter using the value

and it's a key value pair.

So you have to provide

both the things.

So let's just say I have a variable I

and this initially gets

a value of zero and that's it.

And by the way, you can click

on the value and understand

this one as well.

Probably not the greatest of the docs

at this time, probably have

to read in the docs directly.

But you get the idea that how

this actually works you simply

go ahead and take the value.

And the best part is this value,

with a lock to safely

share the data across the processes.

So automatically it gets the lock.

You don't have to worry

about the locks and everything.

Now I can go ahead

and use it directly.

Should I show you an example

of this one?

I think yes, that would be better.

Let's go ahead and get

an example on the separate

file so that you can see.

All right.

Not just Q, I have a value as well.

All right, no big deal.

We can have one more 12

and this one is going to be process

and value py Again most

of the code will remain same.

So from multiprocessing we are going

to import the process and let's

also go ahead and import the value.

We will go ahead and create

the same example.

We have the increment,

no, not like that increment.

And you get some kind

of a counter value inside this

and the counter value is going

to come up from this one.

So how does it work?

And again I have to use

main as well if dunder name

is equals to dunder main.

So the way how it works is

you simply go ahead and create

a counter variable.

This time it's going to be created

by value and you can

create as many as you like.

You just have

to provide key value pair.

So I have a value I which

initially gets a value zero.

But anybody can come

in and change the value as well.

So in My increment method, I go

ahead and run a long loop loop.

So I will say for dash in range.

All right.

And we will go for 100,000.

Good enough.

And now here's the beauty.

I can go ahead and say with

counter that you are passing me.

I can just go ahead and say dot get

lock So I will directly get a lock.

I don't have to actually bring

in the lock and everything.

I know that I'm locking the value

in and I can go ahead

and say counter whose value

is going to be plus equals one.

Now don't worry, I will walk you

through how to pass on the arguments

and everything on that.

You just have to be careful

that what you are passing on.

So this is the only part of it.

Rest is kind of exactly same.

So we get the comprehension,

we go ahead and say process,

something will be created.

We'll create this a little

bit later phase.

First of all for something

in range and we will let

just say create four processes.

And now we can go ahead

and create the process.

So I will just go

ahead and say process.

We'll have a target, we just

have one target increment.

But we also have to

pass on some args.

There we go.

Arguments, which is a tuple.

So I'll pass on your counter

with a comma, of course.

And I will store everything

in processes.

There we go.

Process needs to start as

well as join as well.

So let's write more comprehensions.

So P start and of course a simple

loop for pin processes.

Same goes like there

and this one join.

There we go.

We have written this so many times,

should be all happy and easy.

And after that we simply go ahead

and print final counter value.

And final counter value is going

to be counter dot value.

And there we go.

So notice here this value

is not this value.

Okay, we are just getting this whole

object and inside this when we

say.value it gives me this value.

There are other things as well.

You can go ahead and probably

study more onto this.

Nope, this doesn't give

us any value as of now.

All right, let's go ahead and see

that how it goes.

All right, let's run this file again.

Python.

This time it's 11 or 12.

We are on 12 process value.

And there we go.

Will take obviously more time,

but we get the whole 400,000 as

a value started from zero because

now we have four processes.

So each process will go

ahead and work with that.

When the first process will

reach it will get its own lock.

And when the other process will

reach it, will just get the value

and will keep on incrementing it.

So four processes are going to go

ahead and get their own mutual lock.

But the best part is they

are sharing the value.

Each process is able to share

the value, not only just

they are logged, but they also

share the value itself.

Notice here we were facing this issue

that we cannot transfer the data

queue is one of the solution.

Very straightforward solution,

very much being used.

But this is all good.

Now where would you

use the processing?

Now processing is used

at a lot of places.

So imagine a batch image processing

script which load the images,

apply the filter and save them.

Now multiprocessing allow each

image task to be done in parallel.

And this is how most of the Python

based AI, training scripts work.

Multiprocessing, multiple parallel

workers and all of them.

But again, sometimes people

use multi threading along

with multiprocess as well.

But this is the basics, this is

the foundation of multiprocessing

as well as multi threading.

Hope this section has given

you enough of idea and please

do rate us as well.

I've tried my best to make sure

that this course becomes an absolute

gold value standard

for the amount of money that you

are paying for this course.

Hope you've enjoyed this.

If you think more topics should

be added or some more things

to be added, reach me out on

the Twitter or on the YouTube live.

I would love to add more

content on this course.

That's it for this one, let's

**catch up in the next one.**
