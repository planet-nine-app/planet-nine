### Overview

So the layers of what I have been calling "The Stack" are already being built, but I just got diagnosed with covid, and so I figured I'd write down what the plan is just in case.

After the first startup I worked on got acquired, I decided that I wanted to work on the biggest problem I could think of.
So I thought about a problem that everyone has.
That problem, is that everyone could use more money.
So I tried to think of a way to make that happen.

I started off by trying to make a company that would introduce people to the ideas that would start to move the needle, but it didn't work.
To keep with the stack metaphor, I was near the top, and people hadn't learned about the bottom layers yet.

But this stuff's not a company anyways. 
Companies need to be proprietary in order stay competitive. 
But that limits their reach, and thus doesn't allow for me to get _everyone_ more money.
So I changed tactics, and started building The Stack as free open source software.

But enough prattling on. 
Here's what's going on, and here's how The Stack addresses it.

### Discovery, and location, location, location

Pretty much since the beginning of trade, humans have been dealing with the problem of how to let people know about what they're selling (discovery), and where they're selling it (location). 
Pretty early on, humans recognized they could spend some money to make more money by creating visual artifacts that told people what they were selling, and where they were selling it.
These were the first ads.

In the early 18th century when newspapers started being printed, folks realized they could supplement their printing costs by charging for ads. 
Thus the age of content creators began.
The lower price of the paper increased its reach, the increased reach increased the efficacy of the ads.
So long as the ads weren't too intrusive, customers didn't complain, and all was well.

Of course, back in those days, when you needed a new wheelbarrow you couldn't hop on the ol' interwebs and next-day delivery yourself up one. 

This creates a value loop that looks like this:

[a value loop that shows businesses paying advertisers who pay content creators to create value for consumers who in turn buy from businesses](./flow-of-value.png)

Businesses pay advertisers, advertisers supplement the cost of content creation, consumers consume the content and the advertising, and then consumers buy from businesses.

Everyone hates ads.
Let's just get that out the way.
So it's probably not that controversial to say that finding something that might work better would be nice.
But allow me a paragraph or two about why things are as bad as they are now.

Back before the internet, if you needed to find a lawyer, you really had two options: ask around, or hope you came across what you needed across billboards, radio ads, and, my favorite, the phone book.
The phone book was my favorite because of its reach, permanence, and unintrusiveness. 
For $50 or $100 you could reach a whole municipality for a year or more.

If you've never seen some yellow pages, you should check this out:

[a sweet couple of pages of the Ames Iowa yellow pages from 1990, ranging from entries on farm management services, an floow waxing, polishing, and cleaning](./yellow-pages.png)

Depending on how much money you fork over, your business can be bolded, or have a slightly larger entry, but dangit everyone's getting listed in the yellow pages, and in alphabetical order to boot.

#### Google

Then the internet came around, and shortly thereafter a way of finding things on the internet called Google.
Like the yellow pages before, businesses could pay for prominence in search results, but with a few key differences. 

* It was no longer permanent. 
$100/yr became $100/mo then $100/day and so on

* Listings were no longer alphabetical, but rather determined by a proprietary algorithm

* Businesses in Ames were no longer competing with other businesses in Ames, but with any business that could get their wares _to_ Ames.

Advertising has always benefitted companies that are already doing well. 
That's bad for competition, and bad for innovation. 
And thus bad for the consumer.

With the points above, Google has basically created duopolies with nationwide vendors that local merchants can't compete with.
There're the eCommerce giants like Amazon, Alibaba, Mercadolibre. 
Food delivery apps like DoorDash, Grubhub, UberEats.
Google music and you get a list of YouTube Music, Spotify, and Apple Music.
Every one of those categories so meticulously laid out in those yellow pages are now the purview of some small set of tech companies charging rent[^1] on what used to just happen. 

That's what The Stack is trying to do.
Take a (very small) bite out of the Google/Tech Company duopolies, and redistribute that money between the rest of the parties in the loop above.
The hypothesis is that if we can make it much easier for businesses, creators, and consumers to exchange funds with each other directly, then the tech companies become less necessary, and Google loses some of its appeal.

So let's see how The Stack does that.

### Is it really just that we don't have digital cash?

For most of human history, trade has taken place either through bartering, or through some medium of exhange known colloquially as "cash."
Then in the seventies, cash started to be supplemented and replaced by credit and debit cards. 
When the switch to the internet happened, these cards became crucial because you couldn't teleport cash through a modem to a store's register.

Since the sixteen digit card number and expiration date was all you needed to make a transaction at the beginning on the internet, security demanded that card usage be limited to the site that it was used on.
PayPal attempted a more global approach, but it required both integration by merchants, and signin from users to use, relegating it to just another credit card rail more or less.
And even if not, each merchant still requires an account for this, and address for shipping, and another for billing, and so on and so forth.

What's really needed is a way to un-silo the card payment, shipping information, and account info.
That's not really digital cash. 
What we need is the thing we really lost when all our physical media went digital.

## Interoperability

What do these all have in common in the physical world?

[A vhs copy of the classic movie Point Break](./vhs.jpg)

[A cd jewel case for the Ace of Base's The Sign](./cd.jpg)

[A picture of credit cards](./credit-cards.jpg)

Interoperability is a property of a product or system that means it works with other products or systems.
In the case of these three gems, it meant you didn't need to worry about what VCR your parents bought, or what CD player your friend had, or whether the bodega was rocking an Erply or Vend card reader.
There was utility in everyone getting along, and using the same systems.

Then computers came along, and messed all of that up. [^2]

Computers gave us useful artifacts that were instantly portable to anywhere with electricity. 
When you have something like that, if you want to get paid, you've got to create artificial limitations on usability, otherwise folks will just share your code around.

In the beginning these limitations could be fun. 
Large enterprises might have licensing codes, but if you were a small game studio you might do something like reference a certain word on a certain page of your instruction manual to make sure purchases were legit.

Slowly but surely, email grew in popularity.
Some of you reading this might even remember a time when a jaunty, "you've got mail" was a welcome sound.
This gave a consistent identifier, and so many companies chose to draw their artificial limitations around the email boundary. 
By adding a "secure" password, and convincing everyone not to share it by cloaking it in dots, the fledgling software giants of today started digging their moats in the early 90s. 

Now I can't make a playlist for my wife because she has Spotify, and I have Apple Music. [^3]

#### Distributed systems

There has been much todo about decentralization and federation in the computing world.
Some people think it's significant that the computers running blockchains are owned and operated by random people around the globe, and not one central company.
There are also some interesting things happening with federated protocols like ActivityPub which powers the Fediverse apps like Mastodon and Pixelfed.

But they aren't interoperable either. 

You can't use Bitcoin to pay for an Ethereum smart contract, and you can't upload a single photo that proliferates posts across Mastodon and Pixelfed.

Interoperability doesn't come at a system/protocol level. 
It comes at an industry level.
Sometimes it comes out of necessity, sometimes from regulation, but it never comes from being jerks to each other. [^4]

So here's the industry: the internet.
Here's the interoperability: a set of protocols that let _everyone_ engage with the industry.
Use that interoperability to go after an enormous pain point for _everyone_ who uses the industry.
Get _everyone_ paid.

And that's the purpose of The Stack.

And here's what it looks like:

# The Stack

 ___________________________________
|                                   |
|  Planet Nine - Distribution       |
|                                   |
 -----------------------------------
|                                   |
|  The Adversement - Engagement     |
|                                   |
 -----------------------------------
|                                   |
|  The Advancement - Interaction    |
|                                   |
 -----------------------------------
|                                   |
|  Teleportation - Discovery        |
|                                   |
 -----------------------------------
|                                   |
|  MAGIC - Payments                 |
|                                   |
 -----------------------------------
|                                   |
|  Sessionless - Identity           |
|                                   |
 -----------------------------------


Stacks go bottom up, but humans read from top to bottom. 
So The Stack starts with Sessionless at its base, and works its way up to Planet Nine.
This is reflected in the reading order below.

<details>
  <summary>Sessionless - An authentication protocol for distributed identity</summary>

#### Public key cryptography and you

[Public key cryptography, aka asymmetric cryptography][public-key] generally enables three cryptographic capabilities:

* public key encryption, where a public key is used to encrypt a message and only the corresponding private key can decrypt the message
* key exchanges like Diffie-Hellman, where public keys are exchanged and used to create a shared symmetric key for encryption
* digital signatures, where private keys are used to sign messages, and the resulting signatures are verified by the public keys

For the purposes of [Sessionless][sessionless] we're concerned with the last bullet point.

As the names suggest, private keys are meant to be kept private, and public keys are meant to be shared.
It's this sharing of public keys that makes public key cryptography useful for the purposes of distributed systems, and thus interoperability.
To see how, we need to take a quick detour into how authentication works across the internet today.

When you login to a website or app with your email and password, a server somewhere will check those credentials, and if they pass it'll issue some data type that can be used in place of your email and password.
This data type can take different forms, but for the purpose of this doc, we'll just call it a session.
The session then gets sent with subsequent requests to the server, and that is used to authorize the request.

You could imagine a system where several different servers can accept the same session. 
So long as those servers trust whichever server was checking the email and password, they can trust the session too.

This is, in fact, how modern systems are built for most small to medium businesses. 
The backend is a smorgasbord of acronyms: CDNs, CRMs, and multiple SaaS's, hosted on some CSP. 
These are all linked together through a system of API keys, whose usage are ultimately reliant on authorized sessions.

This isn't so bad, when it's some retailer who wants to make sure you can see their whole catalog of graphic tees, but it gets a little squirrely when we start having user created content.
Like if I told my grandma that for anyone to see her carefully curated photo albums they'd have to sign up for some service that spied on them everywhere on the internet, and then served them constant advertisement, she'd probably have some stern words.

And of course you have to do that because even though you can sign in with Instagram into other things, you can't sign into those other things to get to Instagram. 
That's because Instagram gets to choose which sessions it trusts.
And it doesn't trust any because ~that would mean losing some of the competitive leverage that monopolistic behavior affords tech giants~ of like security and stuff.

#### Enter Sessionless

But what if you had something that acted like a session in the sense that you could use it to authorize requests, but didn't require trust?

If you've had to take any sort of IT course, you may remember the three factors of auth:

* Something you know (such as a password)
* Something you have (such as a smart card)
* Something you are (such as a fingerprint or other biometric method)

Sessions use something you know (a password), and exchange it for something you have (a session stored somewhere).
_Sessionless_ skips the first step[^5], and just uses something you have (a private key stored somewhere).
Then instead of a session being sent and checked by a server, Sessionless can send public keys out to servers who care to verify that you have the private key.

Note I've written server_s_ with respect to Sessionless.
That's the... ahem, key.
Public keys can be shared, and so one private key can be used to authenticate and authorize with many disparate servers.

There are A LOT of things you can do with this.
For one you can create distributed peer payment systems. 
It's also pretty much the only way you can establish trusted communications between machines as SSH, TLS, and thus HTTPS uses public key cryptography.

Sessionless is an attempt to make using this powerful tool easy to implement, and useful for those building useful things. 
It's a protocol, which means it is a set of methods that are impelemented exactly the same across different languages and platforms. 

[Here's a small fun landing page with a demo][sessionless.org].

[And here's its repo][sessionless]

</details>

<details>
  <summary>MAGIC - Multi-device Asynchronous Generic Input/output Consensus</summary>

#### At your service

Pretty much everyone who's connecting to the internet is engaging with client/server systems.
A context unaware client (say a web browser that has no knowledge of what's lurking at www.google.com), sends a request to a server, that server performs some series of operations, and then returns to the client what the client needs to care about.
Servers are just computers running programs, and in the beginning they would usually just run one big program called a monolith.

At some point people wanted to start doing more interesting things then just having webpages popup.
With this came a need for accounts, so that the servers could maintain some continuity between when users decided to show up.

Eventually the monoliths got too big for one computer, and people had to start getting creative. 
Since there are infrastructure needs for large numbers of computers to be running that aren't provided by municipal planning, companies with deep pockets built out that infrastructure and allowed people to rent it.

And thus the cloud was born.

Not too long after folks started hosting their software on remote servers controlled by other companies, people started to question if monoliths were the best pattern.
The pendulum swung, and all of a sudden microservices came in vogue.

With microservices, big programs were chopped up into smaller programs, which were run on different computers owned by the same giant company.
Much digital ink has been spilled on whether monoliths are better than microservices, and I have no desire to revisit this here.
But I will say that microservices tend to be preferred by companies with deeper pockets, which means the cloud providers price accordingly.

Having worked with microservices, it always felt like a waste that they had to all live behind our centralized load balancer, and be horizontally scaled across machines that, for all we knew, were sitting right next to each other in some server farm somewhere.
Like wouldn't it be better if we could just host the microservice close to where people would be using them. 
Like a few machines in every city, maybe more in big cities, just serving the people closest to them.

There're a number of technical challenges to making that happen, but one of the big ones is auth.
You don't want to have to be sending people's auth credentials all over the world to be saved on disparate machines.

But with Sessionless, and public key cryptography, you don't have to worry about that.

In fact you could build a whole system of microservices then that were publicly available. 
Like the payphones of yore, they could just sit there in someone's basement serving up requests.

There are plenty of folks out there running servers out of the goodness of their hearts, but I figured if we could figure out a way to pay those people then maybe we could start seriously talking about moving some of the cloud off of the cloud.

And that is what MAGIC is. 
It's a way of tying some input, both a user action, and user funding of some sort, with some output _across some set of machines_. 
And if those machines are servers that people are running in their homes, we have the potential to pay a lot of people some money, as opposed to ~Bezos~ a few number of people money.

And that sounds pretty magical to me.

[Here is MAGIC's repo][MAGIC]

</details>

<details>
  <summary>Teleportation - because the easiest things to find, are those sitting right next to you.</summary>

There's a fun show on HBO called Deadwood.
The main character is a lawful good sherrif who relocates to the eponymous town to start a store with his partner.
It's certainly not the main plotline of the show, but it does evoke the old adage, "if you find yourself in a gold rush, sell shovels."

In the first few episodes you watch them show up to town, _build their store_, and then start business.
That's what it took to start a store 150 years ago.
Let's take a look at what it takes to start a store now.

First let's define what we mean by store.
There are plenty of ways to just go about selling stuff on the internet, and that's what a lot of people do, but just like pre-internet times, it's hard to sell a lot of widgets from your trunk.
What you want to do is get your widgets into a lot of geographic locations so people can find them there.
Those locations, if they aggregate several widgets, sprockets, and so on, are what we'll call stores.

So if we think about internet stores there are the Amazons, Ali Baba's, and Mercado Libres of the world. 
Certain already huge stores have online stores.
There are a handful of maker platforms that are kind of stores like Etsy.
And that's about it. 

Why is it so? 
Because authentication and identity is vertical on the internet so you need to be large enough to take on things like shipping, and customer service, and so on, and then you further need to be large enough for people to want to sell through your platform.
And then since you're big enough to crowd out smaller merchants you can do this part: "With the points above, Google has basically created duopolies with nationwide vendors that local merchants can't compete with."
And then there are no more stores.

Well I don't know about you, but I contribute to this whole problem because I don't want to go to the store. 
I'd much rather sit on my couch, and tap some links to make a jug of Tide show up in a day or two.
But there are two things about that.

1) That jug of Tide that shows up might have come from Duluth for all I know when there are perfectly good jugs of Tide at the grocery store that's half a mile away.
2) If I'm gonna have to get a jug of Tide shipped to me from Duluth, why can't I get shipped straight from Procter & Gamble? [^6]  

Both of these are solved by a somewhat generous definition of Teleportation :).
The first is outside of the purview of The Stack, but the second is what we tackle next.

##### How do we build the store?

So you've invented some new product, let's call it the widge5k.
Let's say it's a great new home automation product.

You've bought the domain, and it's time to get something up online so people can buy your creation.
You craft the perfect website to capture customers.
You do SEO, and all sorts of marketing.
You buy some ads. 

You google home automation to see what comes up:

![A screenshot of a google search for home automation](https://github.com/zachbabb/ideas/blob/main/home_automation.png)

Cool cool cool. 
Amazon, and Home Depot are your competition in the search results. 
Maybe you could sneak in after what, four or five years of grinding SEO every day?
Of course you'd have to have enough scratch to pay for the position too.

Since you just started, you're small, and, while numbers of conveniently hard to come by, the estimates are usually somewhere between 60-80% of your sales are going to come through Amazon.
So take all that money you're spending on ads, SEO, a cool website, etc, and lop off another 15-30% for all of your sales to go through Amazon. 

And now you're in the ol' duopoly pig butchering scam.
Pour more and more money into getting your product listed, until Amazon reproduces it, or gets flooded with knockoffs.

Now if you're in this, the second to last thing you need is one more thing to do, and the absolute last thing you need is one more thing to pay for. 
Well I've got good news and bad news.
Good news, what I've got for you here is free.
Bad news, you do need to do one more thing... but it's like an itty bitty thing.

Your website has your product in some div somewhere that looks like this:

```html
<div>
  <a bunch of cool html that makes your product look real cool />
</div>
```

And what you need to do is change it to this:

```html
<teleportme someMetaDataThatWe'llGiveYou>
  <div>
    <a bunch of cool html that makes your product look real cool />
  </div>
</teleportme>
```

With just this wrapping tag, and a way to trigger an order, your product "teleports" to other parts of the internet where it can be presented and sold.

People can create stores featuring your product.
People can make content featuring your product.
When it converts to a sale, they get a cut of course, but its smaller than Amazon's, and you don't need to worry about creating affiliate link infrastructure. 

How does this work? 
Webcrawlers can go out and grab the html content in the teleportme tags, and that content can be stored in different databases (teleportals) around the internet for different contexts to pull in.
Then MAGIC lets those contexts interact all the way back to you store, including purchases.

And then how do people find _those_ stores?
Same way we've found stores for thousands of years: they're right near where we are.
I.e. in the apps we already use.

</details>

<details>
  <summary>The Advancement - A browser extension that goes on the offensive against advertising</summary>

What is the internet? 

It didn't dawn on me until I was almost thirty years old, an had returned to college that the internet was just a way of connecting computers to each other. 
For much of the time of the internet up to that point, machines were connected via numbers called ip addresses that were literally saved in text files on intermediate machines. 
When I finally put my first "website" on the internet, and saw it was literally just a text file flying from one machine to another, it was like pulling back the curtain on Oz. 

There are two slight hiccups when it comes to shooting files over to arbitrary machines, and having those machines run your code: people don't read code, and people don't know how to keep their machine safe from code being run. 
And thus the browser was born--the perfect way to make the web's code look beautiful, keep the web's code from stealing your files, and doing nothing else...

> the loveliest trick of the Devil is to persuade you that they don’t exist![^7] 

The only thing I've never understood about Chrome is why it took Google so long to make it. 
The perfect data collection apparatus for its main revenue stream. 
Regardless, we're there now.
Two-thirds of all internet traffic happens in Chrome. 

It might seem kind of silly that this is the line I draw on what I'll build given everything below here on The Stack, but the thing is the _code_ I've needed to write to establish Sessionless, MAGIC, and Teleportation is minuscule. 
A single language implementation of all three is just a few hundred lines of code.

Firefox is like 30-40 million lines of code. 
And btw Firefox is already great, and you should use it instead of Chrome. 

So if not a browser, than what?
Well browsers have these things called extensions. 
They're not super well-known because they're kind of an awkward user experience, and they require getting a little more into the computer than many people are comfortable with, but once you've done it once or twice it's pretty easy.
Just needs to be a compelling reason to do it.

The most popular extensions are ad blockers, and that seems a fine place to start given our goal is to destroy advertising. 

Extensions use a thing called a manifest to tell the browser some of what they do.
Google recently changed to a new kind of manifest that they said was "safer."
This manifest changed a couple of things, one of the big ones being limiting extensions abilities to keep and update lists of urls to filter from pages.
[I'll give you one guess what kind of extensions were making use of this feature.][ublock] 

Now blocking ads at their source is a totally reasonable way of doing it, but it does have one issue, which is that you're blocking the revenue of the person who made the site.
Even with my view on advertising, I hate the idea of taking money from a creator more so I don't use an ad blocker, and when I started to try and think of what to do instead, it was keeping the ads generating revenue, while not annoying me that I looked at.

### The live

[In the late eighties, John Carpenter dropped the absolute gem They Live where Rowdy Roddy Piper finds sunglasses that rveals the world as it really is][theylive].
It has aliens, and advertising, and I was like I wonder if I could do something similar, and show everyone what digital advertising really is.

Turns out I can. 

![Here's a screenshot of a website with an ad](https://github.com/user-attachments/assets/be8bdaf8-3aba-46a4-9eb1-1162256fa237)

Here's a pretty standard news site with ads.[^8]
But let's say we replace the ad with an image of an iconic enemy, and make it so that I can "deal damage" to it by tapping it, and that after some amount of damage I "defeat" the ad. 

https://github.com/user-attachments/assets/2351c413-4c48-4e42-9016-7aaab6cf81ba

And now the ad monster is gone, and the webpage reorients itself as though it was never there.

Did you know you could do that?
Neither did I.
But now that I do, I'm like why the heck do we put up with ads at all?

Doing it this way, the ad still gets served, The Mercury gets its money, and rather than having to resist the temptation to find out my IQ, I can fight slimes.
But what if I don't want to fight slimes? you ask.
Well, you can cover the ad with any image: plants, cats, your country's constitution...it's your browser, and you browsin', seems reasonable to let you view what you want.

### It's on like Donkey Kong

There's a thing in political science called [The Overton Window][overton].
It outlines a spectrum where political ideas are reasonable to the political cohort. 
For example, the existence of this Amazon product:

![A tumbler with very hungry caterpillar that says "eat the rich"

suggests that our Overton Window is closer to late 18th century France than... well I can't really think of a time the Overton window was really pro the rich, but the point is, we're not always ready for violent revolution. 

 



</details>

The rest of this is evolving:

* The Adversement - B2B tools for reaching customers _without_ needing to resort to advertising

* Planet Nine - Planet Nine's purpose is to make _everyone_ more money. 
Humans, not corporations.
That's the purpose of this stack.

### Conclusion

I no longer have Covid so my fear of impending demise has gone down, and thus I've left later parts of The Stack vague for now. 
If you wanna chat about them, head on over to [Open Source Force][osf] on discord.
I'm planetnineisaspaceship there.

[public-key]: https://en.wikipedia.org/wiki/Public-key_cryptography
[sessionless]: https://www.github.com/planet-nine-app/sessionless
[sessionless.org]: https://sessionless.org
[MAGIC]: https://www.github.com/planet-nine-app/magic
[osf]: https://opensourceforce.net
[ublock]: https://github.com/uBlockOrigin/uBlock-issues/wiki/About-Google-Chrome's-%22This-extension-may-soon-no-longer-be-supported%22
[theylive]: https://youtu.be/aiMLJAZajxg
[overton]: https://en.wikipedia.org/wiki/Overton_window


[^1]: "Rent is an economic term for any part of the price of a good that isn't directly involved in the manufacture and supply of said good. The business model of pretty much any app or website that sells things on behalf of others is to charge rent. And who pays for rent? Consumers do."
[^2]: "The tremendous irony here of course is that computers are the ultimate device _for_ interoperability, and it's because of that that people set out to make them interoperable. If I ask nothing else here it's for us not to accept that status quo."
[^3]: "Those of you who have never taped over tabs on a casette in order to record some top 10 song from the radio to share with your friends on the bus the next day, to simply not have the option at all 30 years later is beyond frustrating. 
[^4]: "There are a lot of ways of being jerks to each other, and often they boil down to some sort of us versus them. The name Planet Nine is meant to be evocative of an extra-global mindset where the us is quite literally all of humanity."
[^5]: "It doesn't have to. Sessionless isn't an either/or proposition, and you do sometimes need to provide a way for users to recover keys (of which using a password is one of many methods)." 
[^6]: "I don't actually care about Proctor & Gamble, but for products made by smbs and solo creators, having to buy their wares through Amazon's 30% rake is some bull honky-tonky."
[^7]: "Kevin Spacey is mega-cancelled, so I don't want to use his line from the Usual Suspects here although it's certainly more recognizable. Turns out the quote reflects a commonly held sentiment amongst religious wordsmiths of the late 19th century, and I've pulled one such quote here"
[^8]: "When I was doing this I was trying to use The Mercury, a cool free publication available here in Portland, but my url bar autocorrected it to themercury.com.au, which also seems like some sort of small periodical in Australia. I don't know much more about this Australian periodical though, so apologies if it's not cool. It's here just to show what can be done about ads."
