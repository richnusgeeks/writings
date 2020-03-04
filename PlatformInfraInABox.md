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

Q. Interesting, tell me more about how to take advantage of 12factor through the   minimal changes?
A. Ok, let's take a step forward here and then another backward (not Two Steps
   Behind as per Def Lepperd :-)) to understand more. Nothing comes free so are
   the microservices architecture and containerization. Following is an image
   showing [The Microservices Hierarchy of Needs](https://medium.com/@bibryam/microservices-hierarchy-of-needs-151df49fc678) to run microservices with containers <Insert Image Below>:
   
   If we go through the Kubernetes (just ignore it as a platform for containers
   in this section) vertical then we could see many of these needs are required
   in the non-container non-microservices world also to create manageable, more
   intelligent and less painful systems. Didn't we require Self Healing,
   API Gateway and Service Security, Service Discovery and Load Balancing,
   Centralized Logging and Config Management, Health Checks and Recovery etc. in
   non-cloud native infra? Yes, we required these necessary pieces always as per
   different urgency deadlines but achieving those wasn't easy or folks were in
   hurry to build in ad-hoc ways or something else.

   You could think of containers as the mechanism providing two main advantages
   out of the box: first, an *immutable universal packaging format* which works
   out of the box everywhere running over GNU/Linux, Windows and Mac OS. Second,
   it gives us the capability to *limit computing resources* to pack and run
   multiple components together in a more efficient, robust and controlled
   mannner. You should consider using containers to unify and simplify your
   automation tooling required even if you are not using containers for your
   application services, on your journey towards cloud native.

   If you need to do it similar in the non-containers only VMs world, then first
   clearly define each server structure in form of *server roles* e.g. what all
   versioned components it's suppossed to pack and mechanism to verify those,
   what are their runtime configurations and mechanism to verify that at runtime
   etc. Then we need to ensure that all the runtime processes are subjected to
   the various resources limits ensuring no process is unbound to steal all the
   resources from the other processes responsible for the overall good for the
   VM. It also requires some inbuilt self-healing process baked-in to keep on
   resolving the failures. Finally, you generate the various roles machine
   images based upon their respective baseline structure of components and
   configurations are oulled from a central registry of configurations and
   the servers have the required mechanism to pull the necessary configs and
   apply those to the processes.

Q. I heard this concept of self configuration and healing in the context of
   containers many times but never saw it in the VMs world?

A. Yes, the dynamic nature of containers with an orchestration ecosystem around
   it accomplish the auto config and healing out of the box as those are the
   necessary building blocks already embedded within the containers
   orchestrators. You might have heard about [GitOps](https://www.weave.works/technologies/gitops/) which is a cloud native methodology based upon the same idea
   to propagate changes automatically from a centralized single source of truth
   to the infrastructure pieces pulling and applying the changes. Similar could
   be done in the VMs world through a framework which provides the capabilities
   of indexing the config from a single source of truth and the associated
   agent running on VMs providing config templating and some processes
   orchestration functionality. 

Q. You spoke about servers but didn't mention configuration management even at
   a single place, why?

A. Any [configuration management tool is an antipattern](https://hackernoon.com/configuration-management-is-an-antipattern-e677e34be64c) most of the time in the
   cloud native world. You need those tools only during the creation of machine
   images (and maybe some edge cases like some after-provisioning needs in long
   running stateful roles). Old ways of always trying to keep on imposing the
   desired states for your servers through the config management tools and then
   keeping on fighting with their idempotency promises and eventual convergence 
   only gave birth to the immutable infra pattern. We also need to ensure using
   lightweight push mode config management tools to cut the unnecessary
   complications of managing those just to cater a small functionality in the
   cloud native lifecycle.

Q. You mentioned verification mechanism multiple times during defining various
   server roles, why?

A. So simple, if you can't verify it against the unnecessary baseline then you
   can't prove it correct. The test driven development has been the mantra in
   the software for the last many years so why shouldn't it be considered
   necessary to platform/infra components in the age of IAC? These verification
   mechanisms form different stages of [acceptance testing](https://en.wikipedia.org/wiki/Acceptance_testing) to cross various gates in the cloud native journey
   of taking software from a concept to the final delivery and deployment. Those
   also form parts of the [observability](https://en.wikipedia.org/wiki/Observability).

Q. It's a bit confusing that the verification mechanisms are gonna form parts of
   the observability?

A. Ok, let's talk about only monitoring and alerting aspects from the
   observability world. In a common usage, the monitoring and alerting is the
   combined mechanism to measure some state of a running system and notify the
   drifts based upon the state baseline. But what about ensuring everything
   that forms a role is also in place and good till and after a server reaches
   to the running state? We need this whole start to running state transition
   data to reason out if all good and if not then deriving clues. In fact, the
   monitoring and alerting mechanism at each transition state of a server is a
   prerequisite not the after-thought requirement in the cloud native world. In
   other words, even an empty server requires its monitoring and alerting
   baked-in to throw the red alerts first and then we keep on filling the
   necessary components and configs to establish its green desired state.

Q. Why are you crazy about Free Open Source tooling in the age of hosted
   services?

A. It's not about any particular tooling but exploring and zero upon the
   necessary functionalities first. Nothing beats the FOSS tools to start
   working on the goals right away with full control avoiding any resistance or
   other unnecessary blocking requirements like money, access policies etc. The
   hosted vs running your own comparison is the next step and that's always
   based upon the cost, time and features comparison. Anyway, [the cloud is just
   someone else's computer] running on the FOSS :-).

Q. Ok, what are the necessary criteria for choosing the tools for the cloud
   native world?

A. We need a proper balance between the features provided and the efforts to
   run and manage the tools. So the operations simplicity is also a very
   important criteria as the tools should work for us not vice versa. Also
   the cloud native thinking is being a pessimist regarding the cloud based
   distributed systems due to the [Fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) and even Amazon CTO
   says [Failures are a given and everything will eventually fail over time](https://www.allthingsdistributed.com/2016/03/10-lessons-from-10-years-of-aws.html).

   So we need to keep at-least 2 (Plan A/B) choices to avoid single tool of
   failure and better we keep 3 choices (plan C as well) to follow the
   [CAP theorem] inspired <Insert Image for Good-Cheap-Fast>:

   The cloud native tooling is declarative in the majority of the cases; you
   express you intentions of what to do in terms of the building blocks provided
   by the tooling and the tooling decides how to do it. It's a departure from
   the traditional procedural tooling where you need to encode everything in
   terms of how to do it. Practically, any good tooling provides from 50-80% of
   the functionality required to fulfill all the desired use cases. The rest we
   need to fill in so it's very necessary to consider the extension capabilities
   of the tool in terms of the declarative api, as a main criteria.

Q. What tooling is required for the GitOps kind of self configuring and healing
   infra in the VMs world?

A. First you need a repeatable mechanism to create versioned machine images
   consisting of the necessary configs with variabled through [packer](https://github.com/hashicorp/packer) which ...

Q. You are crazy about the acceptance testing for everything. Now show us the
   cloud native ways to do that?

A. Sure, fasten your seat belt for our journey into various acceptance testing
   options. Here are our options, starting from the simpler (few hours/days
   kinds of effort) to complicated (few weeks/months kind of effort):

   Plan A is GOlang based ServerSpec alternative tool for validating a server's    provisioning. It's driven by YAML description of the acceptance tests you
   want to perform against a server. The same project also provides a shell
   wrapper known as DGOSS for the docker containers validation as well as
   another wrapper DCGOSS to validate the docker containers based upon
   docker-compose manifests. Operationally, goss is a static binary for
   GNU/Linux which is just a grab, drop in a machine and all ready to validate
   our VMs/containers.

   The goss binary needs to get copied to the machines if you are validating
   your VM based server roles as it works in local mode only. So it's
   preferred to bake it into your base images which are used to bring up the
   VMs. The [goss community contributions](https://github.com/aelsabbahy/goss#community-contributions) provide some additional addon functionalities/plugins for
   it including few for ansible and a [packer plugin to run goss as a provision step](https://github.com/YaleUniversity/packer-provisioner-goss) to impose
   minimal acceptance testing at image build time only. It currently [supports many resources](https://github.com/aelsabbahy/goss#supported-resources) to model
   various abstractions provided within a GNU/Linux based machine e.g. *package*, *file*, *port*, *service*, *command*, *process*, *kernel-param* etc. Each
   resource with its relevant properties is included in a yaml (or json) file (by default, goss.yaml but configurable) to create the whole acceptance testing
  manifest against which the goss runtime validation is executed. The quickest
  way to create the initial goss manifest is using [autoadd](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md#autoadd-aa---auto-add-all-matching-resources-to-test-suite), on a machine with the correct desired state (or editing
  the resources properties after generating if desired state is not met), to add
  all existing matching resources. Further resources to this manifest could be
  added through goss command [add](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md#add-a---add-system-resource-to-test-suite). It also provides
  [templating](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md#templates) in its manifest to allow for dynamic or conditional tests and populating
  variables supplied from environmental and/or a vars file. During validation,
  it provides retries with a configurable delay in-between and an overall time
  out as well as configurable output reporting format e.g. *documentation*, *json*, *[tap](https://en.wikipedia.org/wiki/Test_Anything_Protocol)*, *nagios/sensu*, *rspecish* etc. Last but not the least, the goss provides an option to expose
  your [test suite as a health endpoint](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md#serve-s---serve-a-health-endpoint) listening on your
  server on a configurable port. It has a pretty nice [manual](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md) to explore it in more details.

  Now let's come to the dgoss for acceptance testing our containers images. The
  dgoss wrapper script [run](https://github.com/aelsabbahy/goss/blob/master/extras/dgoss/README.md#run) launches a container using the provided docker image,
  copies goss binary and its test suite to that container, runs the goss
  validation in the container and finally deletes the container. The script also
  provides an [edit](https://github.com/aelsabbahy/goss/blob/master/extras/dgoss/README.md#edit) command to install the goss binary into the container and drop
  you into the spawned container shell where you could generate test suite
  automatically through autoadd/add. Once you quit the container shell, the
  generated goss test suites are copied back to the directory from where the
  dgoss was launched. The dgoss also takes [env vars](https://github.com/aelsabbahy/goss/blob/master/extras/dgoss/README.md#environment-vars-and-defaults) to
  alter its behavior. You should create a [driver container image](https://github.com/richnusgeeks/devops/blob/master/InfraValidation/scripts/Dockerfile_DGoss)
  packing goss, dgoss (optionally, dcgoss too), docker static binary (optionally, docker-compose too in case putting the dcgoss) to launch your dgoss test
  suites mounted from here, to use that in your automation pipeline.

  Below shown are test run screenshots (just for a quick feel) from the driver container to run a bogus test suite (generated through autoadd in a container
  with sshd running) against a test image <Insert Images Below>:

  Plan B is the daddy of most of the acceptance testing tooling proposed in this
  doc, known as [inspec](https://www.inspec.io/). It's a very feature rich
  extensive framework which turns your compliance, security and other policy
  requirements into automated tests across containers, machines and cloud
  resources. It provides a DSL based upon ruby to create test suites to make use
  of currently 80+ resources covering from OS to AWS/Azure/GCP level aspects.

  Some not so good parts of the inspec are: its a bit complicated ecosystem and 
  reliance on ruby which is not a fast runtime in case of resources exceeding
  hundreds and [current lack of scan parallelism](https://github.com/inspec/inspec/issues/3010).

  Plan C is a container specific FOSS framework from google folks known as
  [Container Structure Tests](https://github.com/GoogleContainerTools/container-structure-test) which they used internally before releasing it publicly, as per
  their [blog post](https://opensource.googleblog.com/2018/01/container-structure-tests-unit-tests.html). It's similar to the goss operationally, being a drop
  n play golang static binary to use natively or in a conatainer (recommended way, a [driver container image](https://github.com/richnusgeeks/devops/blob/master/InfraValidation/scripts/Dockerfile_CSTest)). It's also a declarative framework
  utilizing the yaml (or json) to model the tests around running commands and
  comparing their output, files existence and their content, and container
  metadata. You don't require the docker engine to run its file/metadata tests
  as the framework provides a tar driver in addition to the default docker
  driver. It also converts the docker image under testing to an in-memory
  filesystem and could perform containers content examination even for images
  without a shell. Having the [goss kind of resources in this framework](https://github.com/GoogleContainerTools/container-structure-test/issues/234) along with
  its metadata testing features would make it a complete tool providing
  declarative acceptance testing for containers.

  Plan D is a bit different from the tooling proposed till now as it's a
  procedural framework, not our desired declarative one, to accept test
  provisioned machines and docker images. But still [testinfra](https://github.com/philpep/testinfra) is a useful python framework to mention here. It aims to
  be a more featureful [serverspec alternative in python](https://testinfra.readthedocs.io/en/latest/) and is based upon powerful [pytest](https://docs.pytest.org/en/latest/) testing engine.

  Plan E is actually not a finished framework or tool but a golang library known
  as [terratest](https://github.com/gruntwork-io/terratest). It provides a
  variety of helper functions and patterns for common infrastructure testing
  tasks, including: *Testing Terraform Code*, *Packer templates*, *Docker images*, *Executing commands on servers over SSH*, *Working with AWS/Azure/GCP/Kubernetes APIs*, *Testing Helm Charts*, *Making HTTP requests*, *Running shell commands* and much more.

Q. You mentioned bringing up the whole stack anywhere but what about the public
   cloud dependencies?

A. You got it correct, the journey is towards bringing the whole stack (or max
   of it, practically) anywhere including laptop and in-between ci/cd. There are
   FOSS components available to mock/simulate the cloud provider services which
   are useful to unblock us at different stages on our cloud native journey. In
   fact, now all the cloud providers have realized it and officially are
   providing ways to play with some of their services locally. AWS currently
   provides [aws-stepfunction-local], [aws-iot-greengrass],
   [aws-codebuild-local], [aws-ecs-local-container-endpoints] and
   [dynamodb-local] for in-a-box testing. GCP [bigtable, datastore, filestore and pubsub](https://github.com/richnusgeeks/devops/blob/master/CloudInfraMocking/scripts/Dockerfile_GCPEMU) all could be [launched locally through a docker container](https://github.com/richnusgeeks/devops/blob/master/CloudInfraMocking/scripts/create_gcpemulators_stack_docker.sh). There is a very [featureful](https://github.com/spulec/moto/blob/master/IMPLEMENTATION_COVERAGE.md) and active python
   library Moto (logical guess, Mock+boto) which also provides a [stand-alone server mode](https://github.com/spulec/moto#stand-alone-server-mode) to run it
   with other languages.

   The most complete open source solution (wrapping many other aws mocking/simulation) FOSS components including moto) to run 20+ AWS services locally for
   integration testing is [Localstack](https://github.com/localstack/localstack).  Below is the block diagram taken from their [page](https://localstack.cloud/) <Inset Image Below>:
