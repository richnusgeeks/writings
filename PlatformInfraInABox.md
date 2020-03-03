# Platform/Infrastructure In a Box

Q. TL;DR (Too Long;Didn't Read)?
A. The practical guidelines, patterns and lightweight open source tooling
   options to be able to launch, run, test, use the whole platform/infra
   stack anytime/anywhere including your laptop.

Q. Sounds amazing but is it possible?
A. The Free Open Source Software makes everything possible, believe me :-).

Q. Great but why did you mention the laptop to launch, run, test, use the
   whole stack?
A. The answer lies in the modern principles of creating platform/infra which
   is scalable, secure, self-service, agnostic to any infra provider,
   intelligent etc. These principles are denoted by a term CloudNative and as
   per [CloudNativeComputingFoundation Charter](https://github.com/cncf/foundation/blob/master/charter.md).

   Actually, the CloudNative principles are based upon some practical design
   patterns known as [The Twelve Factor App](https://12factor.net). In fact,
   the roots of 12factor lie in the age old problem of IT; imparity, coupling
   and complexity. So let's touch these to build more clear background and
   reference those in the later sections:

   Imparity denotes the drift between software versions, configs, processes etc.
   while taking the software from development to production which in-turn
   becomes a big headache sooner than later. It shatters the idea of a
   necessary baseline to compare against to make the things indeterministic. We
   all could easily recall the scenarios where Dev did something, QA did
   another, other guys did their black magic further to keep on declaring the
   software successful at their respective stages of delivery. But finally, the
   Prod busted due to the unknown manual tricks and black magic. So who could
   forget the time wasting painful war rooms sessions on a regular basis and
   always wondering and struggling to reason about the weird failures and doing 
   dirty patching and other black magic to make it work by hook and crook. These
   problems gave birth to the [Immutable Infrastructure](http://chadfowler.com/2013/06/23/immutable-deployments.html) pattern, to make things as deterministic as,
   in-form of [12factor dev-prod-parity guideline](https://12factor.net/dev-prod-parity).

  Coupling presents another challenge to the software world which hurts
  scalability (the most important requirement of every software business now,
  no scaling no survival, so simple). In addition, if the software components
  are tightly coupled then it inherently gives birth to another daemon known
  as dependency hell which makes the whole software componental stack a house
  of cards. The tightly coupled dependencies enforce vertical scaling which
  collapse the resulting software house of cards sooner than later. It also
  wastes a lot of resources to keep the software running through ad-hoc ways.
  The whole notion of microservices came from the intention to remove this evil
  tight coupling and modularize a software stack in-form of loosely coupled or
  totally independent services evolving as per their independent needs and SDLC.
  The birth of 12factor [Dependencies](https://12factor.net/dependencies) and
  [Config](https://12factor.net/config) patterns are the solution to break the
  coupling and support the immutability to enhance scalability through
  [processes](https://12factor.net/processes) and [concurrency](https://12factor.net/concurrency) guidelines of 12factor.

  Complexity is another unnecessary beast which turns every piece of software
  into a nightmare to maintain and keep running. It equally wastes time,
  resources and money. As per Martin Odersky, the designer of Scala programming
  language, [The greatest difficulty in software engineering is complexity](https://www.youtube.com/watch?v=YXDm3WHZT5g). So all the modern best practices of
  software engineering is to break the inherent complexity generated due to
  externally visible imparity and coupling etc. So now we should be on the same
  page regarding the laptop factor of the clud native. Starting the cloud native
  implementations from laptop will ensure that our cloud native journey is gonna
  be as fruitful as possible with we picking lower hanging fruits at the same
  time by instantly empowering and unblocking our Devs, QA and other
  stakeholdrs.

Q. Seems better now but how to fit containers and infra as code in this picture?
A. Glad it came up sooner than later in this discussion. In fact, the containers
   are the magic bullets which provide us the out of the box immutability due to
   their BuildOnceRunAnywhere nature. Those are the basic unity of delivery now
   and automatically introduce the cloud native principles to be followed
   around them as prerequisites (we are killing multiple birds from the same
   stone).

   Now every piece of infrastructure is a software component (Infra As Code)
   and it means that each component needs to go through a full SDLC life-cycle.
   So it requires us to plan in advance how we'll verify and declare various
   pieces good to get consumed in the whole infrastructure puzzle? In other
   words, now we need accepatnce criteria to establish a baseline for all of our
   infrastructure pieces and need to detect, analyze and minimize the drift from
   the baseline definitions.

Q. Does it mean doing Dev(Sec)Ops?
A. Suggest you not to use the Dev(Sec)Ops jargon in the cloud native world as
   most of the industry folks abused this jargon to [cover up ad-hoc work](
   https://blog.gruntwork.io/5-lessons-learned-from-writing-over-300-000-lines-of-infrastructure-code-36ba7fadeac1), similar to [now dead agile methodology](https://pragdave.me/blog/2014/03/04/time-to-kill-agile.html).

Q. It seems the cloud native requires a lot of investment from the beginning
   but I'm in a hurry?
A. Everything needs an investment including being on fire in war rooms every
   now and then. But that's a recurring cost and pain to see everything
   collapsed eventually. The cloud native is an incremental investment which
   provides large recurring benefits once the basic 12factor pieces are in
   place.

Q. So applying 12factor patterns require containers and converting everything to
   the microservices architecture, correct?
A. Microservices are the ultimate goal of cloud native journey and containers
   are a big help towards that goal. But you don't need to boil the ocean and
   12factor patterns could be applied to the non-container world too. In fact,
   existing running software stack is never ready for the containers and
   microservices, most of the times. The container and microservices are only
   the better ways to solve imparity and coupling problems respectively.

