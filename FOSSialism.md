# FOSSialism

The following concerns a set of free, open source repos and services, which are self-hostable, and deployed for use by everyone.

I had these grand plans to have this awesome write up of all this stuff, and how it’s gonna change the world, but I ran out of time. 
So here’s kind of a shortened version with links if you want to read more.

Years ago I got really interested in asymmetric cryptography (aka public key cryptography) for authentication. I wrote a paper for an ACM conference where I outlined how it could be used in a “smart” city to allow people to move around the city and interact with different things. [Identity paper for smart cities][smart-cities].

Being a startup guy, I started a company called Planet Nine, built the system, and tried to get people to use it.
That failed miserably.
I could enumerate the reasons why, but like I said: no time.

I spent the next few years on real life things, culminating in the birth of my son.

Faced with the eventuality that he may ask me one day what it was I had done to make the world a better place for him and his generation, I didn't want my answer to be, "well I moved a bunch of Jira tickets to protect shareholder value, and then I got laid off."

The goal of Planet Nine was always to bring people in to an ecosystem, which would then pay them back for being in the ecosystem.
Turns out you don't need a company for that. 

## The pieces as of Labor Day (US) 2024

There are a lot of names in all of this.
Here are the three most important ones:

* [Sessionless][sessionless] - The public key authentication protocol that everything else here uses

* [allyabase][allyabase] - The public BaaS that Sessionless enables

* [The Stack][stack] - The set of open source protocols built with and on top of Sessionless that enable, among other things, profit sharing from transactions.

### Sessionless

The tl;dr of these three is that the public key authentication of Sessionless lets you create "users" _without_ PII (email, passwords, google ids, etc), which in turn makes it so that you can make services, which are _interoperable_.[ht1]

Having developed a few things here and there, I find pretty much all libraries needlessly complicated, and therefore challenging to use. 
This is largely due to feature growth as products mature, and while I understand the need, I lament the lack of simplicity this constant growth undermines.
I'm not sure anywhere feels this more than the realm of cryptography. 

OpenSSL is a good and noble project, enabling a great many things, but goodness the barrier to entry is _high_. 
Check out this intro page: [ossl-guide-libcrypto-introduction][openssl].
Some complexity's all well and good in libraries that let you add confetti to your webpage, but get this part wrong, and hax0rs will steall all of your users' stuff.

I wanted a library that developers could just drop into their apps, and start using public key cryptography, and so we made Sessionless.

You can read more about how it works in its repo, for here I'll just say it replaces the shared secret that is a session[^1] with a cryptographic key pair where the private key is stored with your client (or in a cookie if you're on web), and where requests are signed by that key instead of sending the shared secret with each request.

Since the server checks requests with the user's public key, and the public key is, well, public, user's can "register" with other servers.
This property of public key cryptography, and thus Sessionless is what enables the interoperability. 

### allyabase

So I started making apps with Sessionless, and as you do, I made some backend services for these apps.
And as is often the case, these services were the same things I'd made, or seen made, or talked about making in interviews, or read lousy blog posts about how to make them, or seen "indie hackers" selling SaaS platforms for, over and over.

So I was like, you know, people can just use Sessionless to connect to these services, why not make them publicly available? 
No signup, no API key, just drop in the client sdk, and use it.
I started to research some of the BaaS providers out there, and was astonished at the gall of gigantic advertising, and eCommerce companies, at charging _you_ for the privelage of sending _them_ all your users' data for _them_ to profit from. 

Humans don't handle big numbers all that well, and so we've let ourselves be convinced that the only way to store the millions of users we're definitely going to attract to our startup is by doing it in some clandestine server farm owned and operated by companies that don't pay taxes. 
Really you can fit those users in RAM on your Raspberry Pi.[^2]

### The Stack

Before I took a sidetrack into allyabase, I was working on The Stack. 
Wanting to continue to utilize the KISS principle, The Stack is a set of protocols, which, is designed to reroute some of the money spent on advertising, and technological rent[HT2], and make it easier for the good people who spend their labor making things (from food to content), to be compensated for their work along with those who do the work of connecting those things with their consumers.

The base of The Stack is Sessionless. 

#### MAGIC 

The next layer is called [MAGIC][magic] (Multi-device Asynchronous Generic Input/output Consensus).
MAGIC is a way of connecting devices, and thus services, together, and then paying out all the participants from the resulting transaction. 
Though it probably sounds like a lot, it's just a structured JSON object (called a spell) that devices can add to along the way, with some terminology (that fits with the magical theme :) ). 
Each thing that's added to the spell is signed via Sessionless so that the resolver of the spell can verify each component.

There are a lot of things you can do with this. 
One of those things is using a microcontroller to cast a spell in a game that a streamer is playing, and paying the streamer when you do, _without_ needing to purchase contrived virtual currencies on whatever proprietary platform the streamer may be using.
We're working on a demo of that, and hope to show it off in a week or two.

Another use case is one near and dear to me, and that is to replace pay washing machines with MAGIC-enabled ones.
The poor tax that is having to go to the bank to get change, and then lug your laundry to the laundromat, or the laundry room in your building, just grinds my gears.

#### Teleportation

The layer above MAGIC is called [Teleportation][teleportation].
It's probably best to read about it, but the tl;dr is we're gonna make up an html tag, crawl for it, and make participants' content available in other contexts.
This way people can make stores, or other discovery mechanisms, add themselves to spell that purchases whatever the teleported thing is, and all this can happen without advertising or search mechanisms.

#### The rest of The Stack

There are three more parts to The Stack, but they're furher away, and not well-defined right now. 
You can get the ideas for them in [The Stack][stack]

## FOSSialism

Woof, this is already longer than I wanted it to be, but I wanted to end on what this has to do with FOSSialism.

So the problem with publicly available software is that, at the end of the day, someone's got to pay for the servers.
The more usage you get, the more servers you need, and the more that costs.
In general, so long as your business isn't selling individual grapes or something, these costs aren't too bad.
But should this get read by more than the three people who read my last post, my server might be in trouble. 

This is why the cloud exists, so that many businesses can share the costs of many servers.
This system enables people to get paid when transactions flow through their server. 
So in my head this enables a public cloud where people can run these miniservices on the computers they already have in their home.

Last year I called my isp because I was having intenet troubles. 
They said I needed a new router, and that that new router would cost $200. 
I said, I will figure out a way for routers not to cost $200.

Here's the way: any computer that sits idly in your home can, at times, serve responses to allyabase, and other Sessionless protocol services. 
With MAGIC that device adds itself to spells that get resolved for money, and just sits there making you money.
Someone makes a line of these household electronics that undercut the non-public serving market, recoupes the difference off of the first 1,000 transactions or whatever, and then you home starts making you money.

If you've watched Shark Tank, this kind of setup might sound familiar: it's how royalties work. 
Royalties are how copyrighted things are supposed to get paid for usage.
You know what's copyrighted as soon as it's produced: pretty much everything creative, but that thing is owned by your company because of employment agreements.
And you opt into that, because how else are you gonna get paid?

This, this is how you get paid. 
Royalties are always shot down because they're bad deal for the entrepreneurs (which they are), but Mr. Wonderful keeps bring them up because they're a great deal for investors.
Anyone who has created anything invested their time, I want to let them get the great deal.

I've been calling this part of Planet Nine [Hedy][hedy][^3].

That's the FOSS part.

### Socialism

There aren't many ism's more loaded than those that Marx coined, but on this Labor Day let's just use this understanding:

When Adam Smith wrote the Wealth of Nations, he said there were three things needed for any business venture--Land, Capital, and Labor.
Back then, land made sense since the economy was largely agrarian.
Nowadays land means anything that isn't money (capital) or human input (labor), which for our present purposes is computers.

These three things describe different economic systems, essentially based on which of the three control the other two.
When the landowners control capital and labor it's called Feudalism.
When the capital owners control land and labor it's called Capitalism (control is obviously a loaded term when discussing human influence over other humans, I suppose here I'm just going to let it be loaded).
When labor controls capital and land it's called Socialism.

If you're American you may know the old addage that starts, "boss makes a dollar, I make a dime..."
Well what if everyone making a dime started splitting the dollar?

## Conclusion 

If you've made it this far, thanks for reading.
It's hard for things not to come off like selling things, but I want to assure you I'm not trying to sell you something here.
I'm just guy with a computer, big dreams, and a plan[^4], and today seemed like a good day to share.


[sessionless]: https://www.github.com/planet-nine-app/sessionless
[allyabase]: https://www.github.com/planet-nine-app/allyabase
[stack]: https://www.github.com/planet-nine-app/planet-nine/The%20Stack.md
[magic]: https://www.github.com/planet-nine-app/MAGIC
[teleportation]: https://www.github.com/planet-nine-app/teleportation
[hedy]: https://www.github.com/planet-nine-app/hedy
[openssl]: https://docs.openssl.org/master/man7/ossl-guide-libcrypto-introduction/#operations
[smart-cities]: https://static1.squarespace.com/static/5bede41d365f02ab5120b40f/t/65d305f9682e3158ed9386cf/1708328441775/ACM+Identity+Paper.pdf

[^1]: "Yes jwts exist too. But they're just fancy sessions because sessions got named first."
[^2]: "Despite our best efforts, humans don't scale with Moore's Law"
[^3]: "Wherever possible I've been naming services after important women in STEAM history, a namespace which seems underutilized in computer science for some reason. Any suggestions for women to honor in this are appreciated."
[^4]: "If Die Antwort would like some royalties, from my usage of a line of theirs here, they can send me their Sessionless public keys :)"

[ht1]: ## "In the hierarchy of non-centralized systems it goes decentralized (like blockchain), then federated (like the Fediverse), then interoperable (like cellular networks, or the world wide web). Interoperability was actually the norm in the years before the internet. You don't have to have different pens for different notebooks."
[ht2]: ## "Rent is an economic term for anything that goes into the price of a good that doesn't come from its inputs"
