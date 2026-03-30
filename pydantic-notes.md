Pydantic is a

standalone curriculum and should

have a standalone course on its

own, but I realized when I'm

making the world's best Python

course, it should be added within

this course.

So within the next few lectures we

are going to study about Pydentic.

I have curated a few good

examples so that you truly

understand the power of Pydentic.

Now, whether you are building for

machine learning, data science,

AI or whether you are building

for web, development using FAST

API or anything similar to that,

even Flask Pydantic is one such

thing that you'll be using quite

a lot.

And in fact these days Pydantic

has launched their own AI model.

Not model, but rather an interface

to interact with the other

models using the Pydentic

they call it as Pydantic AI.

We are not going to be talking

about Pydantic AI yet.

We will be focusing on the core

of Pydantic, what it works

and why is it important

and why everybody loves Pydantic.

Now, Pydantic, some of the people

you will see who comes from the

other programming background, they

call it as equivalent of zod in the

JavaScript ecosystem or some even

say it as a typescript of Python

ecosystem.

Whatever you say, the whole idea

behind Pydentic is simple to avoid

unnecessary errors and stops you

from having the typing error not by

the means of typos but sometimes

some data fields needs to be string

and probably accidentally you have

marked that as datetime or maybe an

integer.

So these kinds of obvious mistakes

are avoided using Pydenting.

It's a fantastic resource.

We're going to together study

about it and you're going

to absolutely love this.

Let me take you onto the screen

and together let's discuss about

the Pydantic that how it works,

what goes behind the scene of

the Pydantic and how it

everything behind the scene of

the Pydantic.

First of all let's go on

to the Pydantic website.

So as soon as you land up

on the Pydantic website it

actually takes you onto Docs.

I just searched on the Google

Pydentic and the very first link it

took me was onto this Docs link.

Now Pydantic has other Things

like base model, model

installation and stuff.

But first of all, this link is here.

There's also a why Pydantic link.

We will study that part as well.

But this is how the Pydantic

initially looks like and it

is very much not clear

that why should I use it.

The website looks boring,

no diagrams, nothing.

But it's a really interesting thing.

So notice here the whole idea

behind Pydantic is this.

It is hard to know why,

many people, let's forget that type

hints, powering, schema validation.

This is the whole point and whole

selling point of pyranting.

I know this is very cryptic

as of now, but as we go further

this will become much more

clear, as with my examples.

All right, so what is Pydantic?

Let's answer that.

So Pydantic is a Python library

that provides two things for you.

The first thing being

data validation.

And there is another thing

which also it does, which is

rarely being talked, but it also

does that thing which is known as

setting management.

Now what is this setting management

and what is this data validation?

Data validation means again, if some

data needs to be of type string,

it should be always string.

It should not change its type

from string to integer

or integer to string.

Setting management is something

that you see more often into web

APIs, especially in the fast API,

whether you want to learn, load

some configuration files, or maybe

you want to load some of the env

files.

In those cases the setting

management works much better.

But the whole job of Pydantic is

to have the data validation.

And as well as setting management,

we will be focusing majorly

on the data validation part of it.

So, data validation.

So we will be walking

through with that.

So apart from the data validation,

it also can do actually data,

parsing, which we are going to see.

And of course the validation

is the key value or

everything that it does.

It is also used in API development.

We will see that especially

with the FAST API.

I'll give you a brief tour

of that as well.

It is also being used

in configuration management.

We will also go ahead and see that

Management management.

And you will also see that sometimes

we use it for data serialization

and of course deserialization.

Please excuse me, the spellings

that I might have mistyped

here, but that's the whole

part of the data validation

that we'll be doing.

All right, so I think this

doesn't still gives you the much

more idea of what Pydantic is.

In simple words, pydantic allows you

to stopping the errors of data

interchangeability of its type A

data for example, let's just say we

have a data which is name the name.

Let's just say I add as

Hitesh, this is a string.

So obviously the data that I have

in here it is string and I

expect it always to be string.

Now there is nothing as of now in

Python which I go up and says that

hey, this can be something like 87.

It is totally possible

and Pydantic allows us to not

do these kinds of things.

That's the whole job

of Pydentic, that is it.

It looks really simple as

of now, but as you go and build real

production application you realize

that these type annotation is

much much important and super

helpful as we go further.

So let's go ahead and set up a simple

application or a simple folder

for us so that we can work on this.

I will call this one as 14,

we're quite in depth of it.

And let's call this one as Pydantic.

And let's go ahead and open

up an integrated

terminal into this one.

Oh, we have some other terminal here.

So let's go ahead and open

the integrated terminal

and first thing that I'll go

ahead and do that is Python.

Let's go ahead and use a module.

I was thinking of using

the UV but I'll create

another videos for uv.

Don't you worry on that.

And I will say we want virtual

environment and we are also going

to call this one as Venv.

Let's go ahead and get

virtual environment.

Hopefully that's going

to do this fast.

Let me quickly check this.

Yep, it does it really nice.

And then all I have

to do is activate this.

So I'll just go ahead and say Source.

Inside the Venv I do have a bin

folder and inside that I do

have my activate script which

actually activates everything.

After that I'll go ahead and say

hey Python, let's go ahead and not

just the Python, actually we can

now use PIP install and upgrade.

Upgrade and pip,

come on, I can type that.

And there we go.

Hopefully the PIP gets installed

and after that I would love

to have a simple Pydentic install.

So I can just go ahead

and say PIP install.

In fact it would be better

to go ahead and see that how

do we actually install this?

So let's quickly go ahead

and see the installation.

Pretty simple.

PIP install Pydantic in case you

are using uv.uv add pydantic.

I'll show you the uv part a bit later

on I will try to add more of these

lectures, on UV as well.

But I think this is good enough.

Pip install Pydentic

and hopefully that is it.

Pydantic is installed and is

now ready to be worked on.

I will go ahead and create

our files inside this folder.

So I'll just go ahead and say let's

create a new folder into this one

because I don't want to keep on

creating too many Pydentic folders.

I will call this one as 01

and I'll call this one as Basics.

And inside the basics I'll just go

ahead and create a new file and I

will call this one as first model

py and in this I will just go

ahead and say print start of

Pydantic.

Journey looks good.

Can we go ahead and run this?

I think I can just click

on this button as well.

This will hopefully run this,

but I'll not take the risk.

I'll just go ahead and say,

hey Python, go inside the folder

of 01 Basics and run this.

And there we go.

We are all set with the Basics

up and running.

Now all I have to do in the next

video is to get you started

with the code part of Pydantic

and we can just learn with that.

So hopefully this video has

given you enough of idea that.

All right.

At least this much I know

that Pydantic helps me

to avoid these kinds of errors

and it is a useful library.

It is used for data validation

as well as settings management.

These are some of the use cases of

Pydantic that eventually I'm going

to learn in this entire section.

But that's it.

That is all for this video.

Let's go ahead and catch

**up in the next one.**



Let's go ahead and continue

our journey on Pydantic.

In this video I'll take you

onto the code file.

We will study some of the code

and we'll understand what we are

writing, why we are writing and why

that is so much of important.

Now the way how you start working

with Pydentic is first and foremost

you import the pydentic.

Let's go ahead and say from

Pydentic no suggestion.

That's weird.

Pydentic we are going to go

ahead and import base model.

Now since this is not giving me

any suggestion which is not really

good, I would love to change

my interpreter, address here.

So for this I can open up my

terminal and can say pwd

for present working directory.

I'll go ahead and change

my interpreter.

Copy that command shift p or

control shift p if you're on

Windows and and go ahead and

just say I want to select the

interpreter and I will go

ahead and give you the path of

interpreter.

This is the path inside the venv

bin and this is where my

interpreter is and that will

give you the suggestion.

This is much better.

And for the pydantic at least

for initial step we

need these suggestions.

So from Pydantic, there we

go, now we have suggestions.

I want to go ahead

and import the base model.

You will be doing majority

of your task in the pydantic

through the base model itself.

I will show you more

on how to use it.

Now let's go ahead

and create a class of user.

This is a simple user.

Every time we want to utilize

the power of Pydentic you simply go

ahead and just say hey, I will

inherit the base model class here.

Now inside this class we don't define

the functionality, rather we

define how our data will look like.

So my data will have an id.

The type of the data of ID

is going to be integer.

After that I probably

will have a name.

The type of this name

is going to be string.

And further I will have a field

which will be is active.

Now this is active will be a field

of boolean and that's it.

That is your pydantic class.

First we will study this

a little bit more.

But how do we actually utilize this?

Let's just say we have some of

the input data that we want to add.

The this is going to be a dictionary

and I do have this data id.

Now I have to make sure

this ID is an integer.

I'll go with that,

then I do have a name field.

The name field I know is

always going to be strings.

So I'll just go ahead and say

this is the chai code.

And then I do have the field is

active and as you can see, there are

some, squiggly lines here because it

says, hey, this is not correct.

As long as you don't write it

perfectly, it's always going

to give you these squiggly lines.

And I cannot just go

ahead and say 23.

If I go ahead and use it 23,

this is not going to work.

I'll show you that as well.

But as of now, let's go

ahead and mark this as true.

Now, right now I

haven't used Pydentic.

The way how I use it is

by creating object from it.

So let's just say this is going

to be my user object.

The way how I want to create

it is via the class of user.

Now in this I want to pass

on this dictionary, so I cannot just

go ahead and pass on this input,

data just like this.

This is not going to work.

This is not a valid syntax.

I have to expand the dictionary,

I have to unpack

the dictionary into the model.

So in order to do so I have

to use the unpack symbol,

that is to asterisk.

These are used

to unpack the dictionary.

Now the dictionary will not treat

it as one object, but all

the inside values will be scattered

around and that's how we use it.

Now let's just go ahead and say I

want to just simply print the user

what happens into this and you

will see there is nothing magical

that happens, but the amount of

safety that we have added is

unmatched.

So in this, let's go ahead

and say Python01

and run this and there we go.

It says no, nothing bad,

everything looks good, all good.

But what happens when I go ahead and

accidentally says that, hey, this is

going to be instead of the chai code

as a string or maybe this one as

true, this one is going to be 25

maybe.

So if I go ahead and run this now,

this gives me pydantic error.

This is validation error.

And this is what we really want.

We don't want any data field

to just work like that.

We want some errors if anything

accidentally goes wrong.

Notice here it says input field

should be a valid boolean.

Unable to interpret, input.

This is all about the foundation

of Pydentic, how it works

and how it is being used.

Now let's just go ahead and work

on with some of the key learnings

that we have got via this one,

the first one is always go ahead

and import the base model.

This is the step one.

All pydantic models inherit

from the base model itself.

Then just go ahead and give

the type annotations.

Annotations.

Type annotations are the field

just like we have used

integer, string, boolean.

There are so many of them.

As we go further we will definitely

go ahead and explore them.

Then also at the time of

model init or model instantiation,

always and always use

the unpacked dictionary.

Never pass on the dictionary

just like as the one.

Let's also go ahead and see what

happens when I go ahead and pass

on the dictionary like that.

We would definitely like to see that.

Let me go ahead and change

this to true again

that what happens in this case.

In this case, as you can see, this

is totally wrong because now it's

saying that hey, I was expecting

you will pass me three values.

But reality this whole thing

will be treated as just one object

of or one data type.

And that's not you want to want.

You want something which is unpacked.

So that is always here.

So model initiation or initiation

really means that you should

always unpack the dictionaries or

I will write it here as well.

Always unpack the dictionary.

Then the final thing that we have

got is automatic validations.

We didn't work much on this.

All these data validations,

everything that came up, they all

have their own data types,

error message and everything.

And what happens behind

the scene is when you create a user

instance just like here.

So the moment you create

a user instance, Pydantic

validates each and every

field automatically for you.

If ID is not an integer,

Pydantic will convert it int raise

into an error just like this.

Now again, pydantic will always try

to convert this also.

So it's not like there are

some things which might

actually surprise you.

Pydantic always try

to convert it into integer.

If it is not able to do it, it

actually raises the errors.

For example, if I just go ahead

and put this into a string.

According to so far discussion,

this should be wrong.

But if I go ahead and run this,

everything is fine because pyden

take P behind the scene tries

to convert this 101 into a string

into an integer if possible.

When things goes out

of the hand like 101A, it doesn't

know how to actually convert

this into an integer.

It will go ahead and raise the error

that Hey, I was not able to do it.

So always remember that Pydantic,

will try to convert it

or raise the validation error

if it is not able to do so.

The model ensures that

the data integrity is,

at the point of creation.

That's the whole point of it.

All right, so I hope you are

having a good time with this one.

Let's also go into the next

video and try to create a little

bit more of familiar exercises

with the Pydentic.

**Let's catch up in the next video.**



All right, so let's move further

into our pydantic journey.

The next thing that I want

to do is the continuation

of the last video itself.

In the last video we saw the basics

of foundation of Pydantic.

Hope they are very, cemented

into your memory now.

But I would just take this exact

same thing and we'll give you

an example of how we can design

one more model with the pydantic.

This is just a repetition,

but this repetition is important

for, for our exercise here.

So let's go ahead and try

to build one more thing.

I will go ahead and create a new file

into this one and let's call

this one as, product model py.

That's good enough.

The first thing that we always go

ahead and do this is from Pydentic.

We import the base model.

I highly recommend you

to write this along with me.

This is important part of it.

All right, let's go

ahead and move on there.

Let's go ahead and create

a class of product.

Maybe you are selling some

product on your website.

The step one is always to go ahead

and inherit from the base model.

Now define your product, how

your product will look like.

Obviously it will have a unique ID

that will have an integer that is

going to be of type of integer.

Then we have a name that probably

is going to be of type of string.

Let's just say we have

some price as well.

And the price is going

to be of type of float.

And it could be other

numbers as well.

But I assume the pricing is

going to be in the dot

format, like decimal format.

So it's going to be more

of a float value.

We also will have probably in stock.

Maybe the data is in stock or not.

In this case, what we can do is we

can simply say that this is going

to be a bool or a boolean format.

But with the equal sign I can

assign a default value as well.

Now you don't have

to pass on this value.

If you pass on, we will

respect whatever you pass on.

If you don't pass on anything, we

are going to just go ahead and use

the default value and that's it.

You have defined another model,

in your application.

Now let's do some of the right way

of using the model and let's

also do one of the wrong way

of using the model as well.

Let's call this one as product one.

So in the product one, all you

have to do is use this class.

All right, Now I have an ID which

is going to have a Number one,

fair enough, we have a name.

This name is going to be let's

just say we are selling laptop

and we have some price as well.

So the price is going to be

let's just say 999.99 maybe

in USD I don't know.

And finally I can go ahead and say

in stock and as you can see

the suggestions are popping up.

The suggestions are also one

more very important thing,

very important reason why a lot

of people use Pydentic.

In this case I'll just go ahead

and say true that this is there,

this is a complete valid Pydentic

thing, nothing to be worry on.

Similarly we can go ahead and say

we want to define a product too.

That surely can be done.

In this case we will try

to avoid the default values.

We will avoid to pass

on the values for the default one.

So let's just say ID is going to

be two the name is going to be

let's just say you are selling

mouse and we can say the price is

going to be 24.33 in this case we

are not passing on the value and

this is totally fine and totally

okay.

Nothing will go wrong in this one.

So if I go ahead and say 01 and this

time I want to run product this will

give us no error, this will give us

no output and that's a good thing

because we have just defined the

things.

Things actually go wrong

when you actually try

to do something like this.

If I go ahead and say this is going

to be my product 3 and the product 3

will also come from the base class

of this and in this I'll just go

ahead and say I want to provide a

name, I am selling the keyboard and

that's it.

This is going to give us an error.

Let's go ahead and see this.

There we go.

So it's giving us the valid error

as well as some of the required

messages field, required type,

missing input, name, name, keyboard.

So all these things definitely

they can be improved.

All these error messages we do

have a control onto this one.

But here are some of the best

practices that I can give it

to you with this one.

So the first thing that I will go

ahead and say to you that always use

the type annotations this is non

negotiable in the world of the

Pydentic you always, always have to

use this, always use the type

annotation and also try to use the

appropriate type.

As you will go further you will

understand more about these types.

There are many of them and again,

you don't need to memorize them.

The int is common for us.

The float is common.

We have seen that string we have seen

bool we have seen and there

are others as well that we

are going to eventually see.

No need to worry on that.

And set the sensible default

as well wherever it is required

or it is okay to have

the default try to have them.

And that's it.

And these are all the stuff

that we are going to remember.

Always try to also remember one more

thing that Pydantic tries to

convert the things for you as well.

For example, if there is a data

which is in the string format

1, 2, 3, Pydantic will go ahead

and try to convert this as

a number or as an integer for you.

Now if you have something as true,

Pydantic will also go ahead and try

to convert this for you.

So it will go ahead

and convert this into a true.

If you have something like 123

but the data type that you require

or you need is into float,

it will go ahead and say 123.0.

It will try its best but it's not

always guaranteed that it will work.

It fails more often than you think

for so don't rely on this.

Always go for that.

All right.

I hope you enjoyed this part.

Pretty easy, isn't it?

And don't forget to rate us as well.

I'm looking forward for your ratings.

I want to make this as

world's best Python course.

That's it for this one.

**Let's catch up in the next one.**


Hey there everyone.

In this video we are going to see

about the field in the pydentic

before we go into the field type.

I will still walk you through

with an example that we

did in the last video.

It's a pretty simple example.

You're always going to enjoy that.

Let me take you onto the screen

and we'll design this

example pretty simple.

The same exercise files that we

were using in the last one.

Let's see, we just want

to have a use case of this.

Let's go ahead and design

a simple card data.

How we are going to design that?

We know that in our card data we have

user ID items and the quantities.

So let's just say we call

this one as user ID.

We have to call this as user

ID, which will be 123.

All right, basics.

Then we have some of the items

and we know that the items are going

to be an array, but not any array,

an array of strings.

So this is going to be laptop.

Laptop.

Then we can have a mouse to sell

and probably have a keyboard.

All right, sounds decent.

And finally, we also want

to have quantities.

I don't want to create

a typo in this one.

So I'll just go ahead and paste

this just as it is

and then we can work on this.

This one.

We have to make sure that this

is going to be dictionary.

So this is how we

define the dictionary.

Then it needs to have

a key value pair.

The key is going to be a string.

So let's just say this one is going

to be a laptop and the value

is going to be an integer.

So in this case one.

Let's define one more

which is going to be mouse.

And let's just say two

and one more keyboard.

And that's going to be three.

Really.

But the most important part to learn

here is that in this cart data,

if I have to create an object

from this cart, I cannot just go

ahead and pass it on directly.

If I go ahead and say I want to

create a cart and, and that can come

from the cart, just like this.

I cannot just go ahead and say,

hey, this is my cart data.

This will be wrong.

We have already studied that.

We have to expand this or spread

this and this is how we do it.

And that's it.

No problem at all.

We can go ahead and run

this example as well.

That hey, we want

to run inside the 01.

This is my field examples, no error.

That means everything

is all good and okay.

Now apart from this, I want to walk

you through with one more Thing now.

So we have seen this part here,

but one more major thing.

So far we have seen

only this base model.

It always comes up there,

stays there, nothing else.

But there is one more thing

or one more type that we have

to learn about the pydantic

which is known as field.

This is pretty massive to be honest.

It has so much things which it

does automatically for you.

And the best way would be

to just write an example for this.

So let's go ahead and create

inside a new folder.

I will call this one as

employee model py.

So so far we have seen.

Let's import the typing first because

we have already done this many time

Typing from typing import

option, not this one optional.

And now from Pydentic let's go

ahead and import the base model.

But also if you notice I can put

up a comma and put up a space.

There is so much more that

can come from the pydentic.

We have just touched

the base in itself.

Notice here allow in nan

alias path is alias generators.

Pydantic is really, really

so much the one that we are going

to talk about is the field.

This is also another thing

which is commonly used.

Let's go ahead and create a class.

This one is going to be employee.

Of course the foundation

will remain same.

We will have the base model

just like that, super simple.

But now here's the interesting part.

The ID remains same integer.

But other things can have furthermore

validations in the pydantic.

For example, the name.

The name could be

a simple string surely.

But if you want

to add more validations.

Now here comes the magic

of the field.

You can just go ahead and say equal

to the field.

There we go.

And use this as a method

or a class, whatever you want

to call it as well.

But make sure you add

the parenthesis here.

Now the most common way is to hit

an enter inside the parenthesis

and then first put the triple dots.

I will walk you through

with each and everything.

What does each and everything means?

First let me write that.

So once we have the triple dots, put

up a comma, then add this one.

Then the first thing that we

are going to go ahead and add is

the min length, which is going

to be three in this case.

All right, then we are going

to have a max max length.

This one is going to be 50

some of you, I'm pretty sure you

are able to predict them.

But don't you worry, I'll walk you

through with each one of them.

Then we have the description.

This is going to be.

Let's just call this one as

employee name.

And then we can also go ahead

and add an example which is going

to be let's just say my name.

All right, let's discuss

each one of them one by one.

What's going on and how

is it going on?

The first that you see

is triple dots here.

The triple dot here

indicates a required field.

Very weird, but this is

how it's being done.

Anytime you see triple dot, that

means this field is required.

Then we have minimum length as three.

That means the name must be

at least three character long.

Then we have the max length which

simply says that the name

cannot exceed the 50 characters.

Then we have the description, it

simply says provides a documentation

for the field itself.

Then we have simple example

which shows the example value

for the documentation.

Or maybe the API schema in case

you are building for the web.

Now similarly, we can have one

more field or a couple of more

fields to work on with this.

And that can be a simple department.

If it is an employee, it must

belong to some department.

And here I'll just say optional

and if it is not optional,

the string can come

into this one and there I can

go ahead and say general.

So if no department is allocated,

it's an optional field.

If you don't provide me one, I'll go

ahead and allocate a general to it.

Then we can have a salary

field as well, which obviously

is going to be float.

But here we can use another

equal sign and can provide.

There we go.

Now inside this again, hit and enter.

That's the best thing you can do.

Some people prefer

to write it in one line.

I don't enjoy that.

I feel it cluttered.

I feel it not so much readable.

Triple dots means it's compulsory.

And then I can simply say GE

and then can say let's just say

this is going to be how much?

10,000.

So this simply means that salary must

be greater than or equal to 10,000.

GE means greater than or equal to.

Now there are so many other

things that you can work on

with and as you will go you

will find them quite a lot.

So these field things can be many.

For example, we have seen

the min length.

That's the one of them.

There's also a max length which

are pretty obvious maximum length.

There is a GE field which is known

as greater than or equal to.

There is GT which simply

says greater than.

Similarly we have LE

which says less than or equal to.

We have the simple less than as well.

And we also have Regex, which I

don't recommend you to mess up with.

They can be really, really

complex, but they do exist.

I can't deny that fact.

All right, so I hope you got

the idea that how these things

works and get around with that.

Now field parameters can be of

variety of types, variety of things.

And we can go ahead and do

more onto this one.

For example, this is just geometry.

If you want I can show you

some of more fun

and interesting stuff on that.

But we can do that up here.

So this is my GE 10,000.

That means salary should

be greater than 10,000.

But I can also go ahead

and add something like le

less than or equal to.

And then I can say one so salary will

be less than 100, 000 triple zero.

And I can also go ahead

and add description on that.

Make sure you add a comma

on each one of them.

I'm not writing the code

in itself, I'm just writing

to explain these things to you.

And then you can also go ahead

and add description

that can be something like this.

Annual salary in USD.

Should have used better USD.

There we go.

So you can write the fields just like

this and so much more can be done.

Again I'm just sharing these

examples so that you understand

that how things can be done.

But there is so much

more can be done.

This comes up with as you go

further and try to add more

things, stuff like that.

Now one more thing which

I would like to show you.

Here we have the employee, but I can

add one more classes just to show

you that these things do exist.

What you can do here

is we can import.

We have already imported

the field, but I can also

go ahead and import re.

I don't like to import this.

This is regular expression.

And you can go ahead

and add regular expression.

Just wanted to show

you the syntax of it.

So this is my user.

Of course it's going to come

from the base model itself.

Now in this I have an email field

which is going to be a string.

Fair enough.

And we can go ahead and add

a field to this one as well.

All right.

Now inside this field

I can use triple dot.

That means it's a compulsion.

Now there are particular

things which are provided

by Pydantic so that I can validate

the email automatically.

It's such a common thing.

But here's the interesting part.

You can go ahead and actually

use regex just like this.

And regex can be a simple regular

expression just like this.

Now it's up to you that what syntax

do you want to use inside this?

I've already discussed in the Python

course above when we were

discussing about the regex that

how regex can be imported.

There are websites like regexr

in case you forgot that.

Let me jog your memory.

So there are things like regexr

where you can have

all these pre built regex.

You can just go ahead and copy that.

They have all these options

of PCRE or JavaScript.

What flags do you want to use?

So all of them you can go.

I just wanted to show you that these

things can exist and not just this.

Maybe you can have a phone

which can be of type string but you

can further give it more

superpower by using the field.

And by the way in these cases

you will see most of the people

write them in the same line

because they look really nice.

So regex and then you can have

the regex just like this.

Now if I go ahead and change

this onto the same line, this

will look much better

but I don't prefer it that way.

Just wanted to show you

how cute this looks like.

Very simple but I don't prefer

to use these things just like that.

They are a nightmare waiting for you.

All right, let me also show

you a couple of common

validation that exists and you

might want to use them.

For example you might

have a field of age.

In that case you will have

obviously an integer but that can be

powered by the field itself.

And I'll go ahead and say

maybe this is a compulsory field.

This can be greater than or equal to

0 very common 1 and less than or

equal to just for safety 150 maybe

somebody is too old but I don't

know, he might be using the

computer or not and I can just add

a description.

Add these description they will help

you to produce better documentation.

I'll just go ahead

and say age in years.

Sounds good, sounds decent.

Similarly you also sometimes

have the percentage.

Oops, my bad, I forgot the commas

and should be all okay.

Now similarly you also have

sometimes percentage validation.

Now you might be wondering where

the percentage validation comes in

handy Discounts most common one so

maybe you are having a discount

discount field and the discount is

going to be of type float but we

want to make additional superpower

to it.

That is going to be a field

maybe this is a compulsory field

and then we can have

a greater than equal to zero.

Makes sense.

You always want to have a discount

greater than equal to 0 but also

always less than or equal to 100

we don't want to give more

than 100, otherwise it will be.

We are paying the money, so we

definitely want to avoid that.

And we can further have a description

which can say discount

percentage sounds good.

Now, there are more things that you

can go ahead and work on with this,

but I'll just stop myself here.

I think you have enough

of idea about the field.

This is something that you

should go ahead and explore

in the documentation as well.

I know, I know a lot of people

hate me for saying that, that, hey,

why are you saying that we

should go ahead and read the docs?

In fact, I got a bad review

for that as well.

That when I suggested somebody that,

hey, go ahead and read a little bit

more on the documentation as well,

he said, we bought your course.

Why are we paying you if we have

to read the documentation?

But my friend, the reality is you

have to read the documentation.

These courses are just

your starting journey.

Eventually you have to read the docs.

So please do rate me because there

are a lot of people who rate badly

just because I gave them a good

advice of reading the documentation.

Take care of that.

That's it for this one.

**Let's catch up in the next one.**


Next up, we want to learn

about the advanced

field types in Pydantic.

Now Pydantic has a great way

of providing you these

data types, but it doesn't

provide you all of them.

Some of them you have to import

with the core modules of Python.

What does that mean?

Let me show you that.

So let's take you onto

the screen itself and let me

walk you through that.

What does it mean by that?

So we have seen some of the data

types actually comes from Pydentix.

So for example, if I go

ahead and say Pydantic.

Pydantic.

Pydantic gives you some of the models

and some of the types that you are

going to see comes from the typing.

Now in case you don't know, typing is

a core module of the Python itself

and you can define some of

the data types using both of them.

So if you want to define the data

types, you can just go ahead and use

pydentic as well as the typing

module for both of them.

And then this data type can be a mix

of typing as well as Pydentic.

So it has all the capabilities of

data types of Pydentic and the error

messages and field validations,

but some of the core

elements from typing as well.

I know this sounds a little bit

cryptic, so let me walk you through

and by seeing the code this

will become much, much clearer.

So I'll create a new file

and we're going to call this one as

Oops, looks like I'm

creating in the wrong place.

Shouldn't be creating in here.

Let me go ahead and delete that.

My bad.

We want to create into 01 basics

and this one is going

to be field example py.

So the step one is

to bring stuff from Pydantic.

So from Pydentic we want

to import base model.

And consider this as

always a default.

You will always go ahead and do this.

Now from the typing we can also go

ahead and import other things.

For example, let's just

say I want to import a list

which is like an array.

You can also go ahead and import

the dictionary and you can also go

ahead and import the optional.

I will show you the example

and use case of each one of them.

Let's say we are creating a class or

a base model class for the cart.

The step one is to create

a class and then inherit

from the base model itself.

This has no compromises.

You always, always have to do this.

Then let's just say we

are defining a user id.

A cart is going to

be added by a user.

So let's have this

very basic integer.

No magics, no shenanigans

in this one, but when I go

ahead and add the items,

this is little bit tricky.

I cannot just go ahead and say

string here or I cannot just

go ahead and say integer here.

This is not going to work because

items, whenever you have a cart, you

have a lot of items inside that.

So this obviously is

going to be a list.

But inside the list I will

have the items which

will be of type strings.

So notice here how I was able to

use the list from typing and as

well as I was able to use string

from the pydentic and that's how

you mix and match both of them.

So in our example, what we can see

clearly here, that from the pydantic

I borrowed the string and from

the typing I borrowed the list.

And then finally the example

that I got here is a simple

list which is just like this

and have a string there.

So I hope you got this now that

from how we are actually borrowing

each one of these things

and getting the examples up here.

Pretty interesting, isn't it?


Next up, we want to learn about

the advanced validator patterns.

Now of course they are part of

identity as well, but these are

more of like a use case study or

some examples that I want to

show you that this is also how

these validations can be

implemented.

It's a pretty fun journey.

Let me walk you through with that.

And for this we are going

to go ahead and create a new file.

Let's call this one as

Advanced Advance Validators.

Py of course.

So the step one is pretty

simple from Pydantic.

We want to import at least the base

model, but we are also going

to need field validators.

So at least let's bring them.

So how do we work with them?

The step one, let's just say we

want to create a class of person

and this will go ahead and get

the base model fairly easy.

And the person will obviously

have a first name that will be

of type string and it will also

have hopefully a last name

and that will be of type string.

Fair enough.

Now what I can do is I can

apply field validators here

for multiple of these properties

at the same time.

So I can just decorate them as

field validators and not only

just one, I can actually go

ahead and say first name and I

can also go ahead and separate

it by comma can say last name

as well.

Make sure you type them exactly.

Same.

I have seen a lot of typos, in fact

have done a lot of typos as well.

Don't do that.

Now in this I'll just call this

one as names must be capitalize.

That's the name of our method.

The first parameter that

it takes is class.

And of course

decorators don't get this.

And the second one is the value.

And for each of the value, what

we're going to do is

let's go ahead and say if not V dot

and we can say is title

and it should be lowercase is title.

So it will automatically check

for the title case itself.

And if it is not, then we can just

go ahead and raise the value error.

And then we can say that names must

be capitalize and capitalized.

And in all the other keys we

can just go ahead and return V.

You will see this

pattern quite a lot.

Not a big fan of it because

this V actually runs first on first

name and then on the last name.

In most of the cases you want

to just keep them separated.

But again it's a pattern.

You will see this quite a lot.

So I just wanted to show you

and this is known as multiple

field validation in case you just

want to know the name of it.

Similarly we have the data

transformation patterns as well.

Let me go ahead and add

another class for this.

Let's just say we have a user

this time instead of a person,

and call this as base model.

And we have just one

field which is a string.

Now email could come up

into variety of formats,

variety of cases as well.

Capitalize, uppercase, lowercase.

But in the database I prefer

to normalize it and convert

everything to the lowercase.

In that case I can again

use a field validator.

And this time we have just

the one which is email.

And I can define a normalize.

Normalize.

Should I write it better?

Norma lies.

Yeah, this one looks good.

Normalize email.

And first parameter

is the class itself.

The second is value.

And in this I will go ahead

and directly return it.

But after taking the value

and I would love to lowercase

it, that will lowercase it.

And also I would prefer

to stripe it off so that

all extra spaces are gone.

Again, a really common data

transformation pattern.

This is just one example.

There could be hundreds

of other such example.

Now not only that,

some people prefer to have

validations run before the model.

So this is also another use case.

Let me show you that part as well.

Since we are talking about

the advanced validation,

just say we have a simple

class which is product.

Again, base model.

Base model.

Let's scroll this up.

Now in this one what we want

to do is let's just say

we have a simple price.

Instead of taking price into a float,

we are taking that as a string.

Maybe somebody is giving us

a price in a format which says

something like this, that

hey, price price is 4.44.

Maybe this is how

the price is coming up.

So we can convert that into the float

into this model itself.

Again the step goes.

Field validator, just like this.

On what field you want to run this?

I want to run it into the price.

All right.

And field validator.

Price looks good.

And apart from this what I can do

is I can provide a mode this.

This time I'll show you

a use case of the before.

I've shown you already

how the after works.

When everything is all done

and everything goes there it goes.

But this is where we are

working with the field validator

in the mode before.

Let's just say we call

this one as parse price.

And this takes class

as well as the value.

Fair enough.

And we want to check if is instance

of the value is string.

Then only we want to perform this.

What do I want to perform this?

I want to return a float,

casted value as a float.

But in this value I want to go ahead

and use a method that says replace.

What do we want to replace?

I want to replace a dollar sign with

nothing so that it just gets off.

And then on top of it I can chain

it further to one more replace.

And this time we'll say that if there

is any comma, I should use quotes.

If there is any comma, just go

ahead and replace it with nothing.

I'll show it to you.

So this is what we have.

So remember we have this kind

of a thing, but we could have

something, like this as well.

So I'm just making sure that all

the values are replaced like this.

But again, there should be more

calculation because this

actually will convert into 444.

So probably we don't want to do this.

We want to apply more logic so that

it actually converts into 4.44.

That would be a better one.

But just wanted to show

you that this can be done.

The chaining can also be done.

I'll remove that because that's not

probably what I really want to do.

And I want to convert

this into a, four.

I'll prefer that.

Hey, this is how somebody

gives me the value.

You got the point.

My whole idea was to get the value.

In all the other case we

just go ahead and say

return the value itself.

Super simple, super easy

to work on with this.

Now further, not only that,

you can actually go

ahead and run the complex

model validation as well.

Let me show you with that.

So for this we need to import

one more stuff for this example

from date time.

Let's go ahead and import date time.

All right, so the last example

that I would like to show you is

let's just say we have

a class that says date range.

Again, this one also comes

from the base model.

And we have a, start date, which is

of time of type date time.

And we have an end date, which

is also a type of date time.

Fair enough.

Now I want to run the whole

model validation in this one.

Not the field validation,

the model validation.

Of course it's not going

to suggest me.

I hate that model validator.

Now let's run a model

validation for this.

I'll just go ahead.

This is a nice use case

of after, not before.

So I'll just go ahead and say after.

Now let's just call

this one as validate.

Shouldn't be like that.

This one is going to be validate

date range seems good.

Class will be first input

and we get the values because

we get all the values

when we get the mode of after all.

Right.

So if the values in the start

date is actually less than or

equal to the values in the end

date, in this case we want to

simply raise a value error that

says end date must be after

start date.

Fair enough.

And in all the other case we

can just return the value.

So these are some of the advanced

validation or rather I would say

use case of the validation

that are being done now.

These are just the basics,

but there could be other

business rule validations as well.

I'll not go much into that.

I think this is fair

enough of an example.

That is it for this video.

**Let's catch up in the next one.**


Next up we are going

to use computed property.

Now Computed property is

one of my favorite one.

I use them probably I overuse

them in a lot of places,

but they're actually fun.

This saves you a lot of time

in writing the actual logic when

you're building the application.

A lot of stuff can be done

within the pydentic itself.

Let me show you the example again.

This is one such thing where showing

you or telling you the theory

doesn't really work well.

But showing you the live example

works much, much better.

Let me create a new file

and call this one as computed.

Computed Prop.

I'll write the full one computer

property PY There we go.

So how do we get started

with this one?

Again the starting is going

to be exactly same.

We're going to go ahead and say from

Pydentic we are going to import

of course the base model.

We are also going to import

the computed field.

So we have this one.

And also I'll also bring

one more which is We probably

don't need to bring it.

Yeah, I guess we don't

need to bring it.

I'll show you what I'm talking about.

Let's say we have a product.

This obviously is going

to import the base model.

So far so good.

No problem there.

Then it has a price

which will be of float.

All right.

It also has a quantity which is

also going to be an integer.

Now what I want to do is I want

to calculate the total price of it.

What's the price and quantity?

I surely can do that in my controller

in other places

in the logic, but I can also do that

within the pydentic itself.

This is where the computed property

or the computed field works nicely.

Now not only the computed field,

you also have to wrap it up with

another decorator which is property.

Now this is directly accessible.

You don't need to import this.

Now computed field decorator

marks the field as computed.

That means it will be

calculated on the go.

When you will ask for the field,

it will go and calculate that.

On the other hand, the property

decorator makes this

accessible as an attribute.

Just like you can access

the price, the quantity.

Similarly you can go ahead

and access this computed field,

whatever you name this one,

I'll call this one as total price.

So this total price field

will be accessible directly.

And let's just say we have

to mark this as self and the data

type that you are going

to return is going to be float.

I love to have predictions that

I know what's about to come

outside of this method, I will go

ahead and say return self price

is going to be multiplied by self.

That is it.

Super simple.

I hope that's not

too complex for you.

It's a super simple one.

You have to mark first of all

decorator as computed field

because it is a computed field

and similarly we can mark it as

property so that it can be

accessible outside of this one

as well.

Pretty simple, pretty easy.

Now similar based on this,

let's actually go ahead and

now that you know the syntax

of it, let me help you in

designing a booking form or

maybe a hotel booking kind of

a system for that.

Let's also import one more thing.

Let's actually mix and match

the field computed field base

model everything so that it

gives you more confidence.

Let's just say we call

this class as booking.

Maybe you are booking

hotels or the rooms in the hotels.

First of all, base model,

no exception there.

All right, good enough.

Inside this first of all

we have the user id.

This user ID is of integer.

Fair enough.

We also need a room id.

Fair enough.

Which can also be an integer.

We also need nights that for how many

nights you are booking this up.

This can be an integer field,

but we can also go ahead

and mark this as a field.

Now at a minimum I can just

go ahead and use a dot.

That means it's a compulsory field.

But I'll also go ahead and say

greater than or equal to one so

at least book one day off the room.

Otherwise what's the point of

putting the nights here?

Let's also go ahead and say rate

per night is going to be a simple

float value, whatever

the float value want to provide.

Now can we use some

computed property here?

Of course we can calculate

the final bill of the user

with the computed property.

Simple.

Go ahead and first mark this

one as computed field then

go ahead and make it accessible via

the property.

Fair enough.

And we can go ahead and call this

one as total amount amount.

This is going to be super simple.

Self going to return me a float,

value and then I can just

go ahead and return self.

I need nights multiplied

by self.rate per night.

That is it.

Super simple.

Told you.

It's actually super simple

to work on with this.

And pydantic is not something

which requires too much of

exercise, too much of work.

It's super simple.

Anybody can work on with this.

Want some more example on this?

Let's actually try to use this.

This will give you more

confidence to you.

Let's just say you are creating

a booking object this needs to come

from the booking class itself.

There we go.

We will have first of all a user ID

that's going to be 123 Then we have

the room ID that's going to be 456.

Very creative there.

And then we can have what do we have?

Nights?

Let's just say you're booking

for three nights and you

are also defining the rate

which is going to be 100.

All right, fair enough.

Now can I go ahead and print

something which is computed?

For example, can I go

ahead and say booking?

I want to know the total amount.

There we go.

I can just access this property.

Don't access it like this.

It's not a method,

it's just a property now.

So go ahead and get

an access just like this.

So apart from this, we

can do more fun stuff.

First let me go ahead

and print this one.

So this is going to be

python inside the01.

We are working on

computed properties.

So we can see that.

All right, that's working nicely.

So computed field is

actually included

in the serialization as well.

So let me show you that as well.

So I can just go ahead

and say hey, booking.

I want to just go ahead

and use a model dump onto it.

Once I do this, this is a method,

I will run it and what you're

going to notice that it

gives me the whole model dump.

That what's going on into this model.

So this total amount property

will show up here as well.

So.

So don't get confused.

Yep.

You haven't mentioned this as

a regular property, but this is

a computed property marked

with a decorator as property.

That's why it will show

up inside the dump as well.

Now there are multiple field

validations and properties that you

can go ahead and work on with this.

But I'll keep the video as short

because computed property.

Probably you need some time to digest

this one, but fairly easy topic.

Nothing to worry on

that is it for this video.

**Let's catch up in the next one.**

There's this another interesting

concept in Pydantic known as

field validation, as well as

the whole model validation.

The field validation is something

that you have already seen

with the field that we imported

along with the base model.

But there is a lot more to it

and once you see it, that is it.

You don't have to worry.

You see it for the first

time, you always remember it.

Thereafter, let me take you

onto the code screen because

some things are actually

much easier to explain and help you

to understand, via the examples

and via the code itself.

Let me create a new file

and call this one as

field example Field validation.

Field validation.

PY name doesn't really matter.

The file doesn't really matter.

We need to have something

to write the code from.

This one, let's go ahead and say from

Pydentic I want to go ahead and

import of course the base model and

along with that I want the field

validator, not just the field Field

validator.

Now the way how you use it is

the specific of getting

started remains exactly same.

Let's just say we have a user,

we go with the base model.

Pretty simple, no changes

up there so far.

Let's just say you have a username

and that username is of string.

Now surely you can also import field

here, but maybe you want to do some

customized validation on that.

Now of course not everything

is possible with the field.

That's why the field

validator comes into this.

Now, once you've defined all the

entities that you want to define

in the class, username, string,

integers, IDs, isactive, whatever

you want to design, once you have

done that towards the end of this

class, go ahead and add a

decorator.

Remember we studied the decorator

quite a lot and some people

were asking me in the comments

as well that hey, why

are we learning the decorate?

They are used everywhere.

So inside the field validator, first

of all mark that for which

this field validator is going

to work and name this as it is

whatever you have named this.

So this field validator

works for the username.

If you have anything else, go

ahead and mark that as one.

So inside this now I

can define a method.

Let's call this one as

a username length.

So this one measures or

validates the length somehow.

The first parameter that you

give is the CLS and and the second

one is gets the V.

I will explain you each

and everything, don't you worry.

First let me write that we are going

to simply put an if condition.

If the length of the Value

that we have is less than 4.

Then I would like to

raise a simple value error.

Remember, we studied the errors quite

a lot in depth and this one is going

to go ahead and say username must be

at least four characters.

Did I wrote it correctly?

Absolutely not characters.

All right.

And in all the other case I can

just go ahead and say return V.

Now what's happening?

First of all, let's see what's going

on with each of the things.

Now the first we have is the,

is the at the rate field validator.

This is a decorator.

Hope you remember that one as well.

Now this applies

to the specific field.

In this case we have this

username field, but it could be

any other field as well.

Then we have this class parameter.

This is just a method definition.

I hope you don't have

any issue with this one.

So this is the class parameters.

This is a class method that receives

the class as the first parameter.

So the whole class

is available to it.

Then we have the V parameter.

This is the value being validated.

So every operation that you want to

check it, analyze it, whatever you

want to do, this happens to this.

This is the actual value

which whenever the user will pass

to this, it will apply

to all of this after that.

This is just the checking.

We are checking for the length,

we are raising the value error.

If it doesn't meet the criteria

and if everything goes right,

we have to return this.

This is the most important field.

Without this, nothing going

to work because if you don't

return the value itself, it

doesn't actually get to rest

of the checking itself.

So make sure you return that.

This is the most common mistake.

A lot of people, does this.

So this is your field validator.

I hope this one is clear.

We do have some of the model

validators as well.

Now model validators validate

the entire model and can

access multiple fields

simultaneously as well.

This one is just for

individual field.

Let me show you that one as well.

We can do that in the same,

file itself.

Let's just say we have a class

call this one as signup data.

Of course this one is going to work

with the base model itself.

There we go.

Let me scroll this up.

Let's just say we have

a password field and this one

is going to be a string.

And then we have a, confirm

not plus confirm password.

This is also a field

which is a string.

Now in the model itself I can

design it in such a way that

I can just check the password

validation right up here.

All I have to do Is have

to say model validator.

Have to bring it first.

I wish it could have given me

suggestion, but sadly no.

So I can just come up here and say

I want a model validator.

So we can have.

Let me show you this nice

and easy model validator.

Now for the model validator

you have to provide the mode

in what mode it wants to run.

Now there are a lot of modes on that.

You can just go ahead

and study on that.

There is no suggestion but one

of the mode that we

have here is the after.

So this runs after

the field validation.

So all the fields like

it has to be string.

It will check for the string.

If you have some of these field

validator it will also go through

with that and then thereafter

it runs this model validation.

Super simple.

Hope that's it.

All right.

Oops, my bad.

There we go.

Now in this we want

to define a simple method.

Let's call this one

as password match.

What it does is again it takes

the class as the first

input and it takes the values.

Since this is a model

validator it access all the values

at the same time.

I can just go ahead and say if values

password password is not equals to

values dot confirm password.

If I have done any typo, please

excuse me on that part.

I try my best not to do

it, but sometimes I do.

In that case we can simply raise

the value error that can say

password do not match and we

don't have to do any computation

in our controllers in the FAST

API or anything that you are

building.

And last but not the least,

you have to return the values.

Make sure you do that, otherwise

this will create a lot of

unexpected errors and that are very

difficult to find as well.

So make sure you keep that an eye.

Just to give you one more walkthrough

of this model validator

is something which access

all the values at the same time.

Once you provide the mode after

which is recommended way, then

all these individual fields will

go through and thereafter this

model validator will come up.

The values are pretty simple.

We have the values as parameters.

It access all the values.

If you have five others, it

will access all of them.

You can just use the dot notation

to access that value.

The first parameter is

always the class itself.

It's a self method inside

the class itself and it must

return all the values.

Either raise an error or it

must return the values.

This is the most important thing.

So I hope you got the idea.

Pretty simple one, they are not

very difficult to understand.

But yes, theory wise they look a lot

that why and what's happening.

But once you see

the code part, utilize.

All right, I got it.

Whenever I'll be defining my

models and pydenting, I'll

be super happy with that.

That is it for this video.

**Let's catch up in the next one.**

Now similarly, we

can have quantities.

So once we have the quantities,

it can be a simple

dictionary, in this case.

And this dictionary will

have a string as key

and integer as values.

There we go, super simple.

That's how you mix and match.

Let's go ahead and try

to do one more.

Just as a practice exercise,

let's just say I am creating a blog.

So this is going to be my

blog post again, going

to come from the base model.

There we go.

Now first step is going to be title.

So let's just say title.

This doesn't need any

typing, import or anything.

It can be just a simple string.

Each blog has got its

title, the content.

Super simple.

We can have a string in this one.

Now here comes the interesting

part, which is image URL.

How you're going to have an image.

Now maybe not all the blogs have

the image, there are chances of it.

So in this case I can go ahead

and use optional which comes

from the typing itself.

And if it comes, it is optional,

but if it comes it will be

in the string format and by

default I'll cast this as none.

So this is really nice

and interesting.

So let's discuss some of the key

concept that we have studied so far.

The first one is this concept

that we have studied.

So this is a list string,

a list containing only

strings, nothing else.

Similarly, we do have this dictionary

which is also a string and integer.

This simply says that

a dictionary with the string

keys and integer values.

Simple, isn't it?

And thirdly, we have also

discussed about optional.

Now optional, but a string.

So this simply says that

a field that can be string or it

can be none really simple.

Nothing much to worry on that.

All right, so I hope this has given

you enough of idea about how

the pydantic fields can be used.

And don't you worry, we have

so much more to discuss.

On top of this.

Let's actually do some

of the examples of this one, but in

**the next video let's catch up There.**



Next up, let's talk about

the recursive models or also known

as self referencing model.

So so far we have seen

that in the diagram.

Let's just say we have a model.

So instead of a user model, let's

just say we have a comment model.

Now this comment model looks

okay, we have a pydantic model.

But what if there is also

a further inside model which is

also a comment model?

Yeah, this looks a little bit weird,

but this is a very common thing.

You might have seen the nested

comment where somebody comments

and somebody adds a reply

to it and somebody on that

reply can also add a reply.

So things can go really,

really complex in that.

But this kind of model is known as

a recursive model or

a self referencing model.

And don't you worry, we're going

to learn how to write them

as well in the pydantic, super

easy, let me open this up and add

a new file into this one.

Call this one as

recursive or self reference.

Let's call this one as self

reference PY all right, fair enough.

Now the step one is obviously

to import the stuff, whatever

the stuff is required.

So let's just say first

of all we are going to say from

typing we want to import.

The first one is list and let's

also grab optional and from

Pydentic we are going to go

ahead and import, base model.

There we go, looks good.

Now let's say we have a class

of comment just like

we drawn in the diagram.

And this one takes a base model.

Looks easy.

And further we have an ID which is

going to be a type of integer.

Then we have content and that's

going to be a type of string.

Now comes the interesting part.

How do we actually

handle the replies?

Replies are also a type

of comment, but they might be there,

they might not be there.

The first step is to go ahead

and call them as optional.

But if they are, then they

are obviously a type of list.

What type of list?

A list which is a type of comment.

And yes, I know you are not

a big fan and neither am I

of writing them as a string,

but that's how the syntax works.

And let's just say by default

they actually gets none.

Now this is a lot that we are

unpacking in just one line here

we have first of all

replies that are optional.

They might be there, they

might not be there.

If they are there, then they are a

type of list and list, not any

type of list, not a list, type of

string, but rather A type of

comment itself and the default

value is none.

Now whenever you are doing such self

referencing kind of a thing, one

thing you also have to do is make

sure you have the comment and then

you add a property to this which is

model.

Do we have suggestion for this?

I guess not.

Modelrebuild.

Yep, that's the one.

And make sure you run this.

So what this is first of all this

is known as forward references.

So in the forward references use

the quote in the model name.

That's the first step you

have to keep in mind.

And then we have this model rebuild.

This is required after defining

the self referencing model.

Otherwise you will see crazy amount

of performance degradation.

So make sure you always

keep that in mind.

And then we have the optional

list which can be nullable.

So we have made it none.

That means it is nullable.

And we have the recursive

validations here as well.

So pydantic validates the entire T

structure automatically for you.

And you might be wondering how

can I go ahead and use this?

Absolutely a valid question.

Let me go ahead and walk you through.

So we have a comment which

will be a type of comment.

Just like that, super easy.

Now in this I will have

first of all an id.

Let's just say we have an ID of two,

maybe one, that's fair enough.

And then we have content.

The content is first

comment, very creative.

And then after that we simply go

ahead and say here are my replies.

How does the replies looks like?

Obviously it can be nothing,

but that's not in our case.

If you look at this, this is

an optional list of comment.

Remove the optional part

from your brain.

As of now it's a list.

So there we go, it's a list.

Now what type of list?

Obviously a list of type of comment.

What does it require

to make a comment?

Idaho content and maybe a reply.

So let's just say this one has an ID

and this one says ID is 2

and this should be an integer.

So ID is 2 and then we need

to have a content.

So we have the content just like

this and it could be reply one

and we can have as many as we

like because this is a list.

So I'll go ahead and add this,

like this and I will just go

ahead and change the content.

First of all the ID

needs to be fresh.

So this is going to be three

and this is going to be a reply to.

Now here's the interesting part.

Further down this road, this

can be further nested up.

Did I forgot a comma or something.

Probably yes.

But anyways, we'll figure

out that one later on.

All right, so further down

the road we can have actually

a replies here as well.

And this can also go like this.

So this is a really,

really complex example that we have,

but I still wanted to show you.

So we have a comment

which has an ID and the ID is going

to be four in this case

and let's just say the content

is going to be nested reply.

There we go.

So as we can see there's lot

and why this one is complaining.

Something was not closed.

This means I forgot

something, ID integer.

Let me quickly check.

What am I missing in this?

Oops, my bad.

I'm pretty sure you might

have already seen that

that needs to be equal.

Pretty basic, but yeah, I I actually

had to run this file to see this.

Sometimes you don't see the obvious

errors that are in front of you.

But this is my friend,

real world programming.

That's how you solve them.

A lot of people actually put hate

in the reviews that hey,

you are not well prepared.

No programmer is well prepared.

Everybody just shares

the knowledge just like this.

All right, so this looks

pretty okay and pretty good.

I'll show you more of this.

Just an example like this

in the next video.

Hope this one was pretty okay

and you are comfortable

with now creating any type

of any type of pydantic model.

That's it for this one.

**Let's catch up in the next one.**

Hi and welcome to the early

morning class on Pydentic.

Hope you're having the fun.

It's a new day for me and let's talk

about the nested models in pydantic.

So the nested model, and

especially this particular

lecture is going to walk you

through with the nested model

as well as some of the complex

structure that you can design

in pydantic models.

So the obvious question is

what is this nested model

and what can I do with this?

Nested model allows you to

compose the complex data structure

by embedding one pydantic model

inside the other pydentic model.

This is essential for modeling

real world data relationships.

Just a basic example

that we can take.

For example we have this

user pydantic model.

So consider this as a whole

pydantic model as a user.

But there could be other pydantic

model inside this model itself.

So let's go ahead and say that this

is also a pydantic model and this

is a pydantic model for address.

And yes, address will be validated on

its own parameters and the user will

be validated its own parameters.

So it looks really bit of a complex

that how we are going to actually

do this, but it's actually very

very simple to do all of this.

By the way I have also added all of

this code files on the Python udemy.

You can check it on my

GitHub repository.

Do rate me, do follow me

on GitHub as well and of course

people have started to

spam the pull request as well.

Really really don't like it.

But anyways you get all

the code files up here.

Coming back onto the topic, we want

to design this user and the address

to nested pydantic model.

So let's go ahead and write

the code for this one.

I don't know why I created

this basic folder itself.

We are doing everything inside

this one but anyways let's call

this one as nested model py.

There we go.

Now first of all let's

import the typing module.

So from typing let's go

ahead and import the list

as well as optional.

Some field might be

optional in this case.

Let me go ahead and remove

this so that you can see

the whole thing at one time.

And from Pydantic we are going to

import yes of course the base model.

Now the first step is

to create a class.

We have been doing this

for a while, let's go ahead

and call this as Address.

This one gets a base model.

No challenges, no surprises there.

In this we have a street,

so the street gets a type of string.

All right, fair enough.

We have the city, which also

gets a type of string.

All right, that's it.

That's all what I want

to do in this one.

Maybe let's just add a postal

code as well, just for fun.

So let's say postal code.

This one is string.

In India, postal codes

are all in numbers.

But in the US region,

postal code also includes some

of the alphabets as well.

Further, let's say that I want

to create a class of user, which

of course follows or take

from the base model is derived

from the base model of pydantic.

Inside this, the user gets an id.

Fair enough.

The user also gets a name,

which is string,

but user also have an address.

So I have this address.

Now instead of calling this

address as a string, now I

can go ahead and call this address

as a type of address.

And this type of address is

already defined up here.

This is exactly the diagram

that we have drawn up here.

We have followed

the exact same thing.

So let's learn about

the key concepts here.

First of all, about

the model composition.

The user contains an address model.

This is how we refer to this.

This user contains a reference

of the address model.

Also notice that use, the type

annotations here use the model

class as a type annotation.

So instead of having a type

annotation of string

or integer, we are having a type

annotation of the address.

We also get the automatic validation.

So pydantic validates

the nested structure.

It's going to validate

the user, but it's also going

to validate the address based

on this type annotation.

This is also known as

hierarchical data structure.

So that's also sometimes

being used just like that.

And how do we use it?

That's interesting.

One usage is actually

super, super easy.

Let's just say we have an address

which comes from

a class of address address.

And there we go.

Now inside this address, let's

just say I have a street.

So this is going to be

my street address.

Let's just say 1, 2, 3, something.

Then I have some city.

I of course would like

to use my city name.

It's a beautiful city.

And then I'll say I want

to have a postal code.

So the postal code in my case is

going to be something like that.

Now how do we create user?

Let me scroll that a bit.

We simply go ahead and say user comes

from the user class itself.

There we go, it has an id.

Let's call this one as just one.

Fair enough.

And we'll have a name.

I'll add up my name and this

time it will have an address.

So for the address I'm going

to mark this as an address.

And there we go.

We have taken the address

from line number 16 and added

that into line number 25.

This is how it works.

So this is how our

user data looks like.

Now there are a couple of other

ways how you can actually

bring this user data up here.

Why this one is having issue

because I forgot the commas.

All right, so this is the basic.

But if I tell you that this

is not really the necessary

that how you always should do

it, you can actually change it

to something like this.

Let me call this one as user data.

This is going to be

a dictionary key value pair.

And in this I'll just go ahead

and say the ID is going to be one.

Then I have the name

which is going to be my name.

Then we have ID name and address.

Now further this address, if

you are writing it directly

it needs to be further key

value pair just like this.

And in this we have to add street

and this street is going to be.

Let's just save.

Or we can add three to one something

and I forgot a comma and again

I forgot a comma and there we go.

Okay, so we have a city as well.

I'll add another city and then

we have finally postal code.

And this is going to be 20001.

I don't know if it exists or not.

So this whole user data now can be

passed on while creating a user.

And you know the drill

how it's being done.

A user can be created by this

user class, but I cannot

just go ahead and pass

on the user data just like this.

I have to spread this out.

And to spread this out

I have to use this.

This one actually makes sense.

So now I can go ahead and print

the user and we shouldn't

have any problem at all because

everything looks okay,

let's go ahead and run this.

Although there is no point of

but still I'll try to run this.

So Python, this is going to be 01

and we are into nested module.

So there we go, everything works.

Notice here address is further

looks like this because

it's again a nested model.

But hey, it works.

That's exactly what we wanted.

So this is what we have

in the first video.

Hope it was pretty okay.

Not very complex but, yes, you need

to know about this knowledge.

That is it for this video.

**Let's catch up in the next one.**


Hey there everyone and welcome

to the Pydantic section.

In this video I would like

to walk you through with some

of the advanced nested models.

Now advanced nested

models are nothing.

They're just kind of examples

or use case of how things

actually work in the real world.

The first one that we are going

to discuss about is going

to be the basic one which

is optional nested models.

So I'll just go ahead and call

this one as optional

and again really bad optional.

So what does it mean by having

an optional nested model?

And again it's better to actually

see them in action

rather than just talking about them.

I'll call this one as advance

nested model PY of course.

So the first one in the advanced

nested model, for example,

let's take a basic example.

First of all let me import the stuff.

So, so from Pydantic we want

to go ahead and import

base model and we might need some

stuff from typing as well.

And especially the first

one being optional.

Okay, so here is an example.

Let's just say we have a class

of company and these days a lot

of companies are online.

So not all of them

do have an address.

Some of them works

from the home itself.

So let's try to get

in the same scenario.

The company definitely have a name.

So this is my string

and then there is address.

So address could be totally

optional and that's the one.

But if it do have an address,

then it might be a type

of address in itself.

We don't have that address yet.

We'll bring that in a second.

But if it has an address, that

address should be of type of address

and that can be simply none as well.

Right now we don't have that address.

So we can just bring that address

from the self reference,

not self reference nested model.

Yep, we do have an address here.

So let's go ahead and bring this.

Copy this and go into the advanced

and let's go ahead and paste.

This should be all.

Okay, now so we have this

address space model.

So company might have

an optional address.

It might be there, it

might not be there.

Now similar to, to this,

there might be an employee which

might be a freelancer.

So in that case let's just say

we have an employee.

And this also takes a base model.

Fair enough.

Employee obviously is

going to have a name.

So that's the one.

But maybe it has a company.

It might not have a company.

So in that case also

this is optional.

Did I imported something?

Nope.

This can be optional and it

might be optional, but if it's

not the optional then it

can be of type of company.

And by default we're going

to call this one as none.

And that's it.

That's we call it as advanced

type optional nesting.

So this is definitely.

We are doing a nesting

of address here.

We are doing a nesting of company.

But they are optional.

They might be there, they

might not be there.

Now not only that, there are some

advanced data, types as well

that you can go ahead and use.

So the optional nested

module is one of them.

But there is also something

known as mixed data types.

And what do you mean

by mixed data types?

In case you remember some

of the classes I told you that this

typing module is actually super

interesting and has so many things.

It not just have optional,

it has list as well.

And there's something known as union.

If you remember the diagram,

we draw the diagrams,

there are things like this.

So if I go ahead and show you,

we do have these Venn diagrams,

intersecting each other.

So there are intersecting points.

When we select both of them, they

are union, things like that.

So the union is like we want

to select both of them.

So there could be an example

of mixed data type as well.

Let me go ahead and try to get

the examples in the same line or

in the same file at least.

Let's just say we have something

known as text content.

So this is maybe we're

designing for a blog.

It also takes the base

model super simple.

And let's just say the type is

going to be a string and we can go

ahead and say text super simple.

And yes, this is also

we can write that.

So the type is string

and we're calling this as text

and the content.

I'm just trying to show you variety

of ways how things can be written.

Because I don't want you

to confuse in anywhere when you

see these kinds of things.

Okay, next one is class

and this one is image content.

This one also takes base model

and again we get the type is

going to be a string

and that's going to be our image.

Yep.

This is also one of the ways

so far we have been

writing in this way only.

But this is also another way

of writing the things.

I don't prefer it.

I usually prefer this syntax.

But I don't want you to get confused

when you see these kinds of things.

Yes, some people do

write code in this way.

Maybe you're working

in a company where people prefer

to write this way also.

So I Want you to just stay

with all the things that

can happen in this case.

Now rest of the things, let's just

say we have a URL that is a string.

This is still don't mix

match these kinds of things.

But yes, these do happen.

That's why we call this video as

advanced knowledge on this one.

So there is an alt text

on this one which is also string.

Now here's the interesting thing.

Let's just say we have

a class of article.

An article have both text

content and the image as well.

We get this through the base model.

Now in here, first of all,

article will have a title

which will be a string.

Now the section, the sections

could be a list.

Surely there could be

more things into this.

If it is a list, I can go

ahead and add a union.

Remember this, this one that we

brought up from the typing.

Now union says that you can have

a union, of X and so two things

can be added into this one.

In this case, this can be a text

content as well as an image content.

So it can be a mix

of both the things.

It can be a mix of text content

that we have here and it

can also be image content.

Only one can also be there.

That's also kind of a union.

But then we don't have

a point of having this.

So in our article we have a title

and then we have a section

which can have a lot of images

and a lot of text content.

So yeah, again you probably will

not be using them in this kind

of a very basic architecture.

But the reason that they

exist, that's why I'm telling

you that yeah, sometimes

they do exist as well.

So this is a mixed data type.

There's another thing which

you will see quite a lot known as

deeply, deeply nested structure.

There we go.

So what is this deeply

nested structure?

I'll just keep this in the same file.

Don't want to, but it's not worth it

to create another file.

Let's just say we have

a simple country as a data type

which has a base model.

Fair enough.

A country has a name, string

format and has a code, maybe

flying code or anything that

is also in the string format.

Now further down the road,

let's just say we have a state.

Fair enough.

And in the state we also get the base

model and each state has a name.

Fair enough.

And state also belongs to a country.

So there we go,

we are having a country.

So far this looks okay,

but let's just say we further have

a city and the city

Also is from base model.

And this is where things

get interesting.

A city has a name string.

Fair enough.

But it also has a state and that

comes from the state itself.

Yeah, that's kind of a deeply nested

architecture that we are going on.

We can actually take

it one step further.

We can have an address and again

that comes from the base model.

And what can we do here?

Let's just say we have a street

which is a string.

And then further we have a city

which is a type of city.

Yes because we have.

And then we have a postal.

Postal code and that can be a string.

As you can see things are going

really, really in depth here.

And we have organization

and that also comes from base model.

And yes things are

going quite in depth.

The organization have a name.

So we have a simple string.

Now in the headquarter we can say

that we belong to an address.

There we go.

And then we have branches.

Surely a company can

have branches in this.

We can have a list

and what kind of a list?

Obviously you have a list

of address but it can also be

an empty one we might not have.

So as you can see this is

quite complex and yes this is

what it means when I say

the deeply nested structure.

There's too much of interdependency

and in the real world

project it sometimes happens

because it's a demand of a project,

it's a demand of the application

that you are building.

So organization

is dependent on the address.

The address is dependent on the city.

The city is further

dependent on the state.

The state is dependent

on the country.

I know I exaggerated a little

bit than it's needed to be

but I wanted to show you that

what really it means when I

say deeply nested structure.

And yes it's not very uncommon

to see these kinds of things.

This was too much.

But yeah, these do exist and that's

the whole goal to walk you

through with these advanced

nested structure of the Pydentic.

That is it for this video.

Hope you have enjoyed this.

If you have enjoyed

this, please do rate us.

We really need your ratings

and your love in the ratings.

That's what only is going

to make this course stand out.

That is it for this one.

**Let's catch up in the next one.**


All right, so we've been building

a lot in the Pydentic

and I thought let me share some

of the best practices that we follow

while building these

kinds of models as well.

And again they are not necessarily

that you have to also use them

exactly but these kinds of things

that worked for us, maybe we can

have a small discussion on them.

And I do have a few

of these practices.

So let's talk about them one by one.

The first one being

the model organization.

So one of the best practice is

the define the leaf model first.

This always and always has

worked for us really nice.

So make sure you can also try that.

So in these kinds of example when

we have address and organization

and whatnot we try to define the

leaf node, the last one at the

very first and eventually we

gradually go up and this has

helped us a lot.

Maybe it can help you as well.

Try this and I'm pretty

sure this will help you.

The build upward model is dependent

on the first one as well.

We try to build upwards itself

because it helps us

to define the last node at first

and then we gradually try

to compose the complex model.

So in this case also I showed

you although that we

worked on the country first

but that's not the good one.

If we had to design the organization

I would prefer to have the

organization first being design and

then would break down these things

like this can be a standalone model

on its own, then try to break it

upwards.

That's the one that

I prefer to build.

Now with this there is also

one more thing.

Use clear naming.

This is one of the hardest problem

in the entire programming.

Naming your functions

and naming your models.

But make sure you use them

with the obvious names.

This will help you quite a lot.

And don't use any jargon names like

A, B, C or just random stuff.

Just always give them meaningful.

If it's not meaningful it's not

worth making a model itself.

And also grip the related

models all together.

So for example in this case all

these models, since they just

belong to one of the problem

that we are trying to address,

try to keep them in the same

file, don't try to import them

too much.

That always helps us.

Now obviously keep them modular,

keep them into separated files

but all the meaningful of them

should be in the one file itself.

Now also try to keep the performance

consideration

when you keep these models.

Some of the things may hit the

performance like for example when

you have recursive models or self

addressing models you have to be

very careful Use the model dump,

otherwise you will see the

performance degradation.

So the deep nested

impacts the performance.

Don't try to keep them like five

or six level of nested, you will

see the performance issues there.

And especially with the Python

you have to keep the performance

quite a lot in mind.

Apart from this large list

of nested models.

Consider paginations in this case

of them usually you will not get

this kind of issue most common.

This was one of the case where we

found that in only one application.

But again you won't be seeing them.

So large list of nested

models is very rare.

But if you have this now also be

very careful about the circular

references they come quite a lot.

Right now it's okay, you don't

get it, but that's okay.

This can actually create

a memory heap quite easily.

And by the memory heap I mean to say

it loads up and keeps on loading

up the memory quite a lot.

And especially be very careful

with, with the recursive

references they can be really

really memory exhaustive.

Also consider the lazy loading,

consider the expense

of how things are there

and sometimes when you try to.

When you see for the first time that

hey we can actually do computed

models as well people try to tend

to use them overly, don't overuse

them, be very careful with them.

So lazy loading is one of the

thing whenever you can then it

makes sense then go ahead and

use the computed models but

make sure it is consuming your

RAM and it's consuming your

CPUs as well.

So every single time a model is being

called the computed

models actually get calculated.

Sometimes you probably don't

need them so make sure

you keep an eye on them.

And here are some last and final

data modeling tips as well.

Model real world relationship this

goes for the database as well.

This goes for pydentic as well.

Try to be as close as what you're

trying to build and build the model

based on those relationship only

use the optional appropriately.

Not all relationships are required

and this has saved us so many times.

Sometimes the field might

be empty and try to make

it as close as possible.

As to the database models

this will help you quite a lot.

But not everything needs

to go into database as well.

Sometimes you just want

to check them but try to use

optional as much as possible.

Also don't shy away from using

the union types as well.

Especially for

polymorphic relationships.

And I gave you an example as well.

This is very rare to see in any other

tutorials or any other

courses but we since use them

quite a lot, the union types.

So I thought it's a good idea

to share this with you and always

validate the business rule.

Nothing comes more than

the business rule.

Remember always that we are

building the applications,

the apps, the mobile apps or

web apps for the business.

The business rule takes

the priority than any other thing

even if there is a little bit

of performance degradation.

But there is no other way

of dealing with the situation.

Business rule comes the first.

And that's all I wanted

to say in this one.

So these were some of the best

practices that I thought to share

with them and try to pause the

video and get them one by one that

what is the model organization best

practices?

What are the performance related best

applications that you can

go ahead and do them and what are

the data modeling tips that can

improve your best practices?

Again these are not

hard coded logics.

These are some of the things which

I thought to write them and share

with you as a best practices.

But again best practice is

something that works for you.

That's the whole

underline of this one.

So hope this video was helpful.

That is it for this one.

**Let's catch up in the next one.**


Hey there everyone.

It's a really early morning

for me and trying to record

a few videos before I hit the gym,

before I hit the workout.

Let's go ahead and talk about

the pydantic serialization.

It's not really a pydantic

serialization, but in general

of format of serialization.

And the obvious question is

what is the serialization?

And especially in general if I

remove the pydantic part of it,

what is in general a serialization

that we are talking about?

So serialization is a process

of converting complex

data structures like pydantic model.

So if not be wrong if I go

ahead and say that this one

we can just go ahead and add this

one and go for like this.

So pydantic models.

So serialization is just a simple

process in which we take

the pydentic models and we try to

convert them into something which is

much more easily understandable.

Not understandable, but they

can be easily stored, they

can be easily transmitted or

can be processed as well.

What are these things?

Things like Python dictionaries,

and what else it could be, it

could be JSON strings and it

could be custom format as well.

But I will say XML as well.

We don't use XML that much.

But this whole process of converting

the pydantic models into

all of these formats, that's it,

that's your serialization.

Told you.

It's really, really simple.

Let me go ahead and add a few

examples for you.

Let me close all of this

and now we can actually go ahead

and create another folder.

It would be really nice

to have another one.

Let's call this one as

02/ Serialization.

Serialization.

Did I misspell it?

Yep, serialization looks good.

It's very difficult to spell

out the serialization.

And let's create a new file and call

this one as serial serialization.

Serial JS PY of course

not JS There we go.

Okay, so what are we going

to do in this one?

First of all, let me expand

this a little bit so that

we can see more of this.

There we go.

All right, so how does it start?

It's actually super simple.

We're going to create a pydentic

model and we're going to see that

how we can actually serialize that,

convert that into format, which

are super easy to work on with.

And what are the gotchas moment where

things can go really really wrong.

First of all let's go ahead and bring

pydentic and we want

to import base model from it.

Not only just base model, we also

want to bring in the configuration

dict which is also known

as configurable dictionaries.

A type dictionary for configuring

the pydantic behavior.

And we are also going

to say that from typing.

Let's go ahead and import.

Just the list is fine

enough as of now.

And we're also going to work

with the date time because this is

the most problematic thing while

we work with the serialization.

So from date time, import date time.

Fair enough.

Now let's go ahead and create

a class of address.

I don't know why I'm creating

so many classes of address.

There we go.

This has a street

which is a string basic.

We also have a city which is

also going to be a string.

And we have the zip code or postal

code, whatever you want to call this

one as this one is also string.

Very basic.

Nothing advanced in this one.

Now let's create a user.

This is where we are going to see

things which are interesting.

So let's just say we have a class

user which also gets the base model.

And it has id which is

integer, it has name.

I want to create a decently

complex class so that we can

have a real world example.

We also have email.

I can write that.

And that's going to be a string

is active which is going

to be a Boolean field.

Maybe he's active, maybe not.

Let's just say by default we turn

this as true, that user is active.

And then we have created

at And this one is going

to be type of date time field.

And then we have address

which is of type address.

Fair enough.

And we also have tags for

this user which is going

to be a list of string.

And by default we call it as empty.

Now here's the interesting thing.

Whenever you mark anything as a date

time, this is going to create

a problem because the way how

the datetime works is not very

compatible with any pydantic model.

Most of the time you will prefer

to customize it, configure

it that how it should look

like and how it should work.

And for exactly this we call

something known as model config.

You want to configure this model

and the way how we

configure it is via the config

dict config dictionary.

Here this is a method.

And inside this method we

just have to say we are going

to use the JSON encoders.

This encodes the string in

the format that you want it to be.

So this is super simple

to work on with.

It takes just a dictionary like this.

And we are going to say that we want

to override this date, time and,

and the way we want to overwrite is

by using a lambda function.

Remember we talked a lot

about the lambda functions

in the functions part

of the course itself.

And it's super simple.

Whatever the value we are

going to get is going

to be processed like this.

We will take this value and we

are going to use string formatted,

time strf time and you provide

a format to this one.

Now again, while we provide this

format, nobody remembers this.

I happen to write this so many times

that I remember just one format.

Otherwise you can just look into

the docs and can find that one.

So the first one is all starts

with the percentage so percent d

dash percent and then oops, not

the equals dash percent Then we

have dash percent and each of

these letter have a special

meaning in the formats that we

are doing.

So the capital Y is

of super buttons here.

Similarly we can go ahead and change

the hour, minute and second.

So this is going to be hour,

this is going to be minutes.

Make sure it's a capital one.

The small one is actually month.

And then we have got the second

so percent and capital S.

So this is the format that I remember

because it's an easy one.

Oops, my bad.

This should be a dash.

So there we go.

So we have our date, months and year.

Maybe you want a different format.

You can just go ahead and look into

the docs and, and find that out.

So this is all it takes.

Now the most important part is how

do we actually go ahead and use this

very interesting one.

So the usage part is actually

not that difficult.

Let me show you how it's being done.

So this is my user.

This is going to get from the class

of user just like this.

Let's say we have an ID

of one and needs a comma

and then we have a name.

Let me go ahead and add my name

comma Then we have an email

which is going to be H at the rate

hitesh AI not my actual email.

And then we have created at.

Now this is where you have

to provide the date time format.

So I'll just go ahead and say

this is a date time and now

you can pass on the format.

So I'll just go ahead and say

this is 2024 and then we'll

provide the third and the 15

and then I'll say 14 and 30.

Fair enough.

Now go ahead and study more

about this datetime format.

You can just hover this

and support that.

This is how it looks like

and all formats that it has.

But again not really that

difficult to work on with.

Now let's go ahead

and work on address.

The address is going

to be of type of address.

There we go, just like that.

And in this we have the street should

have the suggestion, but nope,

street is going to be something.

Then we have the city.

Let me check that.

Yep, we have city and zip code.

So we have the city.

I'll add up my city and we have zip

code and that's going to be

009988, whatever that is.

And then we have other fields

as well which is is active.

Let's call this one as false

just to override the value.

And we have the tags which

is an array of strings.

This can be premium user and maybe

he is also a subs, just like that.

So this is all it looks like

at first it looks like very basic.

And what did I missed?

Did I miss some comma?

Yep.

Did I missed more commas?

Yep, yep, looks good.

All now how we can go ahead

and work on with this.

Now there is a special method

of how you actually go

ahead and use this one.

So first of all we are going

to go ahead and take this user

and now we can use methods on this.

The first method that we are going

to use is this model dump.

And notice this, this is abstract

user generates a dictionary

representing of the model.

So that's what we want to use, model

dump and I'll show you what it does

exactly, don't you worry, we will

store this into a simple variable.

Call this one as Python dictionary.

There we go.

Right, now this is not

a true dictionary.

This is very nested

and all these things.

So we'll just go work with this.

First of all, let's see

the output of this.

I'll go ahead and say, hey, let's

just go ahead and print the output.

That will give you more clarity on

what is happening even in this one.

So for Python we are going

to go into 02 and there we go.

So notice this, this is how

it looks like as of now.

But what happens when I go ahead

and try to print the user directly?

That's also a good question.

If I go ahead and try

to print the user and then get.

Let's also get multiply by 30

so that we can see the differences

actually what's going on?

So there we go.

So this is how basically

this looks like.

Notice here the address

part especially.

This looks like, with a format

this is not usable as of now.

But the moment you say model

dump, this actually converts

everything into a dictionary.

So now notice the address part here.

The address is street.

This is in the dictionary format.

And that's exactly what the model

dump is being used for.

Now again we have more stuff

like we have the date, time,

address and all these things going

on pretty nice and easy.

But we can see all things

are looking decent.

Now we can also use one more,

method for this one.

So let me go ahead and walk you

through with that part as well.

Just one more and let

me remove this part.

There we go.

And I can actually convert

this everything into a JSON

string as well.

How can we do that?

We can use the same and we

can say model dump JSON.

This will convert everything

into a JSON.

Like model dump is different.

Model dump JSON is different.

Let me show you that.

First of all, we are going to print

and equal 30 times and then we're

going to go ahead and print this

JSON string so that we can see the

difference between each one of

them.

Let's go ahead and run this.

And there we go.

So right now this one and this

one looks almost exactly same,

but the difference is this is

actually a type of JSON string.

So this is much more usable and you

can, you can go for quite a lot of

stuff that can happen into this one.

So again, remember, there are two

different methods, kind of doing

the same thing, but they are

very fundamentally different.

And with this, to finally

solidify the concept that

what are these two things?

You just need to remember that one

is actually kind of a dictionary.

One is just a ready usable string.

I have actually the documentation

with me so that we'll

just read one line and that

will help you to understand.

Notice here, this is what we have,

the model dump that we used first.

This is the primary way

of converting a model to dictionary.

So notice here, this is,

we are converting a model

to the dictionary.

Submodel will be recursively

converted to dictionary.

That's exactly what we did.

We have converted the sub models

into the dictionary as well.

I hope now the code is making

much more sense to you.

So we have these submodels.

They are also being converted

into the dictionary.

That's exactly what I was

pointing to, this one.

So this is the dictionary, but we

have also another one which

is just written below this.

There we go.

So another thing that we used

Was this one model dump JSON.

What it does this method

Serialize a model directly

into a JSON encoded string.

It is a string but it's

not an ordinary string.

This is a JSON encoded string.

What do you mean

by JSON encoded string?

There are two things.

The simple regular string and there

are JSON which are converted

into the string which can be

converted back into the JSON format.

They are the JSON an encoded string.

And I hope this gives you a much

better idea of how

things are going on now.

Also one more thing which

can actually go really

really fascinating.

First of all look at the output

and then we are going

to see one interesting thing.

Now notice Here the DateTime

DateTime we have this format

up here which we have got.

But what if we don't get this one?

Let me go ahead and comment

this out because you need

to see what happens when we

don't do this kind of a thing.

Let me just comment this.

Fairly simple just control

slash and that's it.

Now let's go ahead and run all

of this output here as well.

Now what you will notice notice it

created at still looks the same.

But here, look at this created at

this is the one I was pointing to.

Notice here how the output

actually goes.

This is 2024 something.

So let me just go ahead and take

this output and bring it here

so that you can easily see

this is the output that we get

when we try to convert it back.

When we see it as it

is, there's no problem.

It looks kind of the same.

So created at date time this is

how the output looks like

in the very first print statement

that we are trying to do.

So this is the first print

the user when you print

it as it is no problem.

But when you convert it into

the dictionary, this is what happens

and here it is date time datetime.

But when you try to convert this

into a string this is what happened.

We don't want that.

So that's why these are

precautionary thing and these are

the best practices that when you

have and once I actually uncomment

this now whenever we use any

method whether it's model dump or

model JSON dump or model dump JSON

then things actually are much more

easier for us.

So we can see now this one

is actually much better.

So created at this one is actually

now in the exact time what we have.

We don't have the dollar we should

have passed on one more variable.

That's why this is actually

saying hey you should have passed

on one more variable.

That's why it's saying and I

intentionally left it, believe

it or not, to just show you that

these things can happen.

Now surely we can go ahead

and add one more thing.

Let's just say we can have 20 up

here, save this and can actually go

ahead and work with this and oops,

looks like we are missing a format.

Let me go ahead

and quickly check this.

We are missing a format.

My bad.

I accidentally actually

put it as this one.

It should be percentage.

Save that.

And now let's try to run this.

And there we go.

We have all the data

being calculated nicely.

There we go.

But again daytime is not something

that anybody can teach on the go.

And this requires a lot

of, lot of preparation.

And even when we work on the real

world data as well, we open up the

documentation at one screen and try

to write these things because who

can remember these kinds of formats

and there are so many formats you

work on with.

This is just the one

that I've told you.

Anyways, hope this was a pretty

intense of a lecture but it

was very useful for you.

This is one of the most important

thing that you'll be doing

with the pydantic model.

Converting them into the JSON

and converting them back

into JSON from the string.

So hope you are now

totally clear about model dump as

well as model dump JSON.

Super interesting.

Read a little bit more on the docs.

At least read this page.

This is not definitely too

hard but the more you're going

to read the better developer

you're going to become.

That is it for this one.

**Let's catch up in the next one.**
