+++
title = "[EN] Monofony"
subtitle = "A Symfony project based on the internal structure of Sylius"

date = 2019-12-26
draft = false

authors = ["Gabi Udrescu"]

tags = ['en']
+++





*Author note: once I saw the [original article](https://afsy.fr/avent/2019/22-monofony-base-sur-la-structure-interne-de-sylius) shared on [Sylius Slack](https://sylius-slackin.herokuapp.com/), I wanted to use this whenever someone asked me what is [Monofony](https://github.com/Monofony/SymfonyStarter), why use it, how can I use Sylius (concepts) in my own application; although initially I planned to just translate it to English, I decided to rewrite it a little bit and adapt it to my needs.*


# The itch


My personal belief is that whenever you have an *itch*, there is someone out there, in the world, who has already had a similar problem and, most probably, already has a solution for that. 

And, instead of reinventing the wheel, you can use your time and energy to build on existing grounds, rather than start from scratch.

Every once in a while, I tend to have *that idea* that excites me to the point when I am able to spend a few nights working on it while still attending my day-to-day job. 

But starting a new project can be a long and tedious job. If you have a great idea you want to put out there in the wild as soon as possible to get feedback and it takes you a full day only to setup such basic functionalities, such as login, forget password or user registration, the enthusiasm will soon fade away. And who wants to do a full setup for continuous integration every single time you start something new? 


# What is Monofony?


[Monofony](https://github.com/Monofony/SymfonyStarter) is a Symfony application scaffold that allows you to bootstrap a modern application by leveraging Sylius bundles and components, helping you to focus more on what truly matters to your use-case, rather than on the underlying infrastructure required to power things up. 

Monofony comes at hand if you:
 - have a public facing part of your application and a backend, only for admin
 - show list of items with filters, sorting and pagination
 - require visitors to login or register on your website to be able to perform certain actions
 - send emails 
 - implement complex business logic for your items where certain states have important meaning and transitioning from one state to another triggers custom behaviour 
 - expose an HTTP RESTful API
 - care about software quality to implement automated testing (unit testing, integration testing or end to end) and static code analysis

Starting a new Symfony application with Monofony allows you to work faster by using built-in functionalities from [Sylius](https://sylius.com), whether you are building a backend, an API or a full stack application. You will save a lot of time by just creating the entities and properly configure grids and forms for them.


# Concepts


Everything starts from the model: the entity. 

> LazyAssTip: I usually create entities by using [Symfony MakerBundle](https://symfony.com/doc/current/bundles/SymfonyMakerBundle/index.html).

Once you created the entities you need, their properties and their relations, you can start leveraging Monofony:

 - declare your entity as a Sylius resource for CRUD operations backend
 - create a grid for CRUD operations frontend
 - create the routing required for the grid navigation
 - add a link to the existing menu of the application as an entrypoint for admin users

## Resource

When I first learned about Resources, my first question was: wtf is a resource and what's the difference between that and an entity?

Well, if you declare your entity as a Resource, the [SyliusResourceBundle](https://docs.sylius.com/en/latest/components_and_bundles/bundles/SyliusResourceBundle/index.html) will provide you:

 - a factory class to build your entity as you need it, so you don't need to `$entity = new Entity();` everywhere.
 - a repository with basic methods to cover adding, removing, paginating and database retrieval
 - a controller for listing entities, showing one item, creating, updating, deleting and even bulk deleting stuff
 - customisations points through Events
 - default forms based on declared properties
 - default routes for HTTP CRUD operations (basic REST API)

So, basically, everything you need to build an admin interface. Now you just need templates.

This is where Monofony saves you time: the maintainers took the Sylius templates and made them more generic, to be able to handle any kind of application.

## Grid

[SyliusGridBundle](https://docs.sylius.com/en/latest/components_and_bundles/bundles/SyliusGridBundle/index.html) is a bundle that takes a previously registered Resource and creates a grid where you can:

 - list entities by using a custom repository method with built-in pagination
 - filter what entities you show in your list based on complex criteria 
 - sort entities as you need

The most powerful part of the grid is that you can customise how they look because every column can be an independent twig template. 

And Monofony comes with good default templates for integers, strings and dates. But you can create your own for rich content such as images, workflow statues or nested objects.

# Customisations

Although Sylius Resources and Grids are coming with pretty good defaults, you can customise them to your needs quite easily:

 - custom factory to provide you entities with valid state from the beginning
 - custom routing
 - custom forms for creating or updating
 - custom actions
 - custom templates

And, you don't need to reimplement everything just to modify some behaviour. You can rely on Events to customise how the app works. 

# Testing

Monofony comes with the following testing infrastructure preconfigured for your usage:

### Unit testing:
 - PHPSpec for Spec BDD
 - PHPUnit for classic unit testing

### Integration testing 
 - PHPUnit with API TestCase extension
 - Behat

### End 2 End Testing
 - Behat with Selenium and Google Chrome setup for Javascript interaction

### Code quality
 - Infection setup for mutation testing with PHPSpec integration
 - PHPStan and PSALM for static code analysis
 - PHP Coding Standard configuration
 - Travis-CI configuration for running everything to make sure your commit is not breaking the existing code behaviour

Now, you really don't have any other excuse not to properly test your application before going in production.

# Monofony is not perfect

There are plenty of solutions out there, in the wild, that try to scratch the same itch. A few that I used and I want to mention:

 - EasyAdminBundle
 - SonataAdminBundle

Compared to Monofony, [EasyAdminBundle](https://symfony.com/doc/master/bundles/EasyAdminBundle/index.html) has a far better documentation and it allows you to start with an easy implementation. But things start to become a little bit tricky when you want to do more advanced stuff such as filters or customization. You either end up rewriting a lot of the EasyAdmin elements (controllers, forms etc.) that you start wondering if it wouldn't have been a better idea to implement it from scratch rather that tie yourself to a 3rd party bundle for good. 

Compared to Monofony, [SonataAdminBundle](https://sonata-project.org/) feels old and outdated, but that's just me, but that mostly because I knew Sonata long time before I ever heard of Sylius and before Monofony was invented. Both lack the documentation EasyAdmin provides, but their flexibility and extensibility make up to that. If you manage to grasp everything and you are not afraid to push your google skills to the limit. 

Monofony might not have that big community behind it, yet, but because it is basically a Sylius without the eCommerce part, you can safely rely on that community for help. And that [documentation](https://docs.sylius.com/en/latest/index.html), as well. 

Monofony, like Sylius, puts a big emphasis on code quality and automated testing. This is something important, especially for a project that might become big enough to matter. And it also helps you learn from others how to easily and properly do programming nowadays, without having to worry about issues that were already tackled. Monofony won't do your work on this end, but it will surely relief some heads aches from your head when it comes to QA. 

Personally, what I also miss in Monofony is a good Docker setup for [development](https://github.com/Sylius/Sylius-Standard/blob/master/docker-compose.yml) and [production](https://github.com/Sylius/Sylius-Standard/blob/master/docker-compose.prod.yml) deployment, especially that Sylius already has a pretty good one already in place. But, that should be addressed, at a certain point, since I started an [issue](https://github.com/Monofony/SymfonyStarter/issues/193) about this. 

# Final words

I have been a product owner for an eCommerce website that relied on the foundation Monofony is built and there have been a few projects I have been in charge of that reached production and performed quite well.

The architecture, the flexibility and the out of the box functionalities provided recommends it for both prototyping and for strong, long term, development. My2c.

[source](https://afsy.fr/avent/2019/22-monofony-base-sur-la-structure-interne-de-sylius)

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzU2NDA0MTI0LC04NjIyMDIwNzksMTkwNz
QyNzU0MCwxNzE2OTkyNjAwLC00NTc2NDQxNjIsMTI3OTIzMTQy
NCwxNTc0OTMxMTE5LDYzMDA4Mzg4OCwxNDA3OTUzOTg1LC0zMT
IxNzMzMDUsOTYzMzM4NzgsMTgzNDQ2OTY1NSwtNTQ1NTA3OTI0
LC0xOTAxODg2Mzk5LC0xOTY3MzA0OTQzLC0xMjY0MTMzMTIsLT
E4NDEwMTk5MDksMTY2Njk2OTM4MF19
-->