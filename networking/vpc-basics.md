 ## Networking on the cloud 
One of the core things when it comes to doing anything in the cloud and I want to welcome first of all all the
so thank you Darko for having me on and I look forward to building with the community yeah awesome so I we brought
2:24
the one on on today to give us some Basics some introductions to vpcs on AWS
2:30
because vpcs are important I see Brandon here commenting saying lots of people like to talk about networking that may
2:35
be correct in our own little bubbles but uh I actually sometimes I'm surprised how
2:42
how some people don't even think about networking on AWS because of course they use a lot of that abstraction on in the
2:48
cloud which is fair which is fair but sometimes knowing a little bit about how things work in the back end is it can
2:54
can take you a long long way so today that's what we're going to be talking about we're going to be covering networking and
3:01
I know Duan has been a um a a very he is a very experienced person
3:07
when it comes to networking all that fun Cisco stuff all the networking uh content Duan has been created Duan has a
3:13
YouTube channel called lab every day so if you're not subscribed go to youtube.com C lab every day and
3:21
hit that subscribe button and check out a bunch of great content created by the one and I wanted him to bring that
3:27
knowledge on this side and talk to you all about and ultimately build something
3:32
when it comes to the vpcs so dwan tell me tell us tell the chat
3:38
um what are we gonna be doing today yeah so today we're going to first talk about traditional networking just a quick
3:44
overview and then what happened to the AWS console to explore the default VPC
3:50
so you can get familiar with actually what's going on with AWS networking from
3:55
a personal and Hands-On the keyboard standpoint the next thing we'll do we'll build on our own custom VPC and then
4:02
after that we'll establish connectivity between the two vpcs with VPC parent
4:08
awesome awesome cool so Back to Basics right and I think I think ultimately let's let's kick it off and talk about
4:14
traditional networking let's talk about how this has changed in the cloud because you know hey taking a step back
4:20
here I thought Network and being the network admin is the best thing ever right when
4:25
I was a young young lad young sister admin I wanted to just do everything with Cisco devices and you know the kind
4:32
of the cloud kind of took that away from me because I kind of started abstracting things but I want to hear how this
4:38
actually works how do you approach Cloud networking in AWS or anywhere in general
4:43
so um I'm gonna I guess I'm gonna share the screen right
4:55
without starting with PowerPoint so let's talk about traditional networking
5:01
really quick all right so traditional on-premise networking what does that look like well
5:08
you first start out with a customer a user or someone like yourself that needs
5:14
to connect to um the internet how does that look well the first thing
5:19
you do is you connect to a switch which is a layer 2 device that provides you like Darko is presenting right there
5:25
access to a network which is local area network yeah now on that switch you're
5:31
going to have something called a VLAN which is basically a broadcast domain for you to communicate with every other
5:37
device that's in that VLAN that local area network now once that VLAN is created you'll
5:44
have a couple switches connected to each other and then ensuring that you don't have anything like a broadcast storm or
5:51
any type of um issues on the let's say local area network you're going to have something like spanning tree to present
5:58
those collisions in that Network now those switches will connect then to
6:05
to routers and something with let's say um hsrp which is going to be a high standby router protocol that's going to
6:13
allow you to have connectivity down two different paths so if one issue if issue happens on one router down that pad you
6:20
can fail over to the other router or you can have like an active active type flow and then at that point you'll connect to
6:26
the internet and so that's how traditional networking looks in a on-premise environment now the
6:33
there's some challenges with this one of the challenges is that this is kind of expensive to scale and what does that
6:40
mean well you got to pay for Hardware you have to pay for another location to
6:45
host that Hardware you have to pay for a service provider to connect you to the internet now you see this is just these
6:53
challenges are happening over um not just Financial capital expenditure but as well as the time that
7:00
it costs to procure that hardware and also to configure and deploy that
7:06
Hardware because often you'll configure these devices one by one yeah and like
7:11
you know this is also also networking is a very physical thing right when we talk about
7:17
servers when we talk about applications you can potentially squeeze more people on a server on an application than
7:23
there's physical space on it but there's only one network plug in the wall and
7:28
that Network plug leaves leads to a one thing on a patch panel and that thing on a patch panel leads to a one port on a
7:35
switch so there's actual physical limitations to how much people can access the network so you
7:40
know it's it's a very hard scalable thing as you say so unlike your traditional other things outside of the
7:47
networking this one is a very rigid scale thing yes
7:52
um there's many challenges Darko you mentioned Port capacity that's a huge
7:58
challenge that we used to face in some of my environments but we're not here to talk about on-premise Network and we're
8:04
here to talk about the Amazon bpc throw away your switches friends don't need
8:10
for switches anymore we still need switches to connect to the internet we still need stuff don't throw them away
8:19
so so AWS networking fundamentals I want to kind of go over this before we
8:24
happen today that was kind of so um if we look if we look at this presentation we have the AWS Cloud
8:30
that's going to be your account when you first establish um your login or
8:35
credentials to AWS now when you establish your account you're going to determine a region that you're going to
8:41
launch resources in um that region is normally going to be as close to your customer as possible
8:47
and then once you establish the region you'll have what you call your VPC or which is going to be your virtual
8:53
private cloud okay so now I I always have I always
8:58
have a question here people you know comparing the actual physical world and
9:03
the cloud World in this case when we talk of VPS about a VPC is a VPC a vlab
9:10
or is that the whole network like you know if we could make draw a parallel here how would that look like
9:16
so if we look at a VLAN that's going to have limitations right um
9:21
your VLAN is basically one big broadcast domain where a whole bunch of devices
9:26
can communicate in one network the VPC is actually going to be a
9:31
virtualized data center so everything that's in the data center from routing to Route tables to
9:38
firewalls you name it two containers and
9:43
virtual machines all of that is going to go inside of your VPC so look at your VPC as a virtual data center where you
9:50
deploy things like virtual machines right right got it okay okay cool thank you all right so I mentioned the VPC now
9:59
once you you create your VPC you'll give it a side of block of
10:05
um up to a slash 16 down to a slash 28 which is basically your IP address range
10:10
for that VPC and you can do ipv4 IPv6 now once you create your VPC the next thing
10:17
you need to do is determine an availability Zone where you'll create your subnets and your subnets that's
10:24
going to be um a small subnet or sub Network for
10:29
your virtual machines right yeah and Summit is defined by an IP range
10:36
right right a smaller IP range of it than your solid block of your VPC right
10:42
now inside of that public subnet you'll launch your ec2 instances inside of a
10:48
security group you can't launch ec2 instance without a security group so that'll be like the firewall for ec2
10:55
instances and that Security Group can be attached to multiple instances as well and I I like that I like that
11:01
explanation of a security group right a security group is basically a state full
11:06
firewall attached to an ec2 instance and that's it yes and stifle meaning that if
11:13
you send a request in One Direction the return on traffic from that request will be allowed through as well rather than
11:19
Knuckles which I don't have display here yeah um I should have put that on here as well but knuckles with the network
11:25
access control list those are going to be statements so you have to put a rule in both directions in order to allow
11:31
that return traffic yep okay awesome we have a question here coming from
11:37
Kevin and uh question it's a question for later but I think it it's it works right now as a cloud developer
11:44
what layers of the OSI model should one care about three three four seven or do
11:50
they need to care about player two as well that's a good question uh we have a say
11:55
in the AWS that layer 2 doesn't exist in the cloud so
12:02
that is this but from a let's say a networking standpoint you need to care
12:07
about layers three and up pretty much so that's going to be your IP address your
12:12
ports and then when we talk about layer seven that's going to be let's say you're using an application firewall or
12:19
albare care about that layer 7 communication flow as well right okay okay awesome now a question for me here
12:25
because I in the past had issues with broadcast noise uh broadcast noise for all of you out there is if you have a
12:31
single big Network just everybody broadcast on that Network asking for ARP uh are sending our packets and all that
12:39
stuff can something like that happen on a VPC that you have like a broadcast storm people just asking for
12:46
um things have you seen that kind of thing no um and that's one of the reasons they say layer 2 doesn't exist because that broadcast communication
12:52
inside of a VPC doesn't use this beautiful beautiful awesome okay continue with sir
12:59
all right so now that we've created a subnet and we created a VPC inside of a
13:04
region and then created a subnet or inside of availability Zone that's inside of our region as well the next
13:11
thing we need the next thing we need to talk about is the route table now every VPC that is created is created with the
13:18
default VPC and that default I mean a default route table right that default route table allows you to say where you
13:26
want your traffic to go it tells the VPC where to direct traffic so in this case
13:32
we have what you call the internet gateway this internet gateway is how we access
13:37
the internet it attaches to a VPC and you'll see here in a moment in the AWS
13:43
console how that actually works but inside of this route table what we'll do is put a route to the internet gateway
13:49
and then at that point if the route table has a route to the internet gateway any subnets that are attached to
13:55
that route table will be a public supplement right awesome awesome and we have a customer here coming in from Gigi
14:02
ajara uh how does the private IP communicate with public IP I guess we'll get to that in a moment right but it
14:08
does involve some math gateways well let's let's kind of move on to that um yeah before we do no notice that um I
14:16
have a router here every VPC has a VP uh VPC router that basically is manages
14:23
traffic for that VPC now this is something you don't really have to worry about AWS takes care of that for you but
14:30
you can kind of direct how the traffic is handled through the route table exactly exactly you the find just the
14:35
route table the router there exists so you don't have to create it provision it manage it nothing like that so that's that's the beauty of it
14:42
um Duan before you move on to the next slide I want to welcome all the new folks joining in the in on stream welcome this is built on weekly and
14:49
episode 16 and today I have the wonderful Duan Lightfoot here he and he's going to talk to us all about AWS
14:56
networking fundamentals so if you have any questions regarding vpc's sublets private and public IPS maybe even on
15:03
that Gateway um just drop them in the chat we see them here and thank you very much for watching and and being part of the
15:09
stream do you want yes so for design scenarios you can look at
15:15
this as a VPC with a public subnet a single public subnet yes
15:21
that's one of the first AWS design scenarios another design scenario is going to be
15:28
a public and private subnet and so how did how does that actually work um it looks like we have a question in
15:34
the chat about how the private IP communicates with the public IP so the way this works is rather than
15:41
having one subnet you'll have two subnets the public subnet will have a
15:47
route will be attached to a route table that has a route to the internet gateway and then you'll have a private subnet
15:53
that have that will have a round table to a net Gateway and so what will happen is any communication that these database
16:01
servers need to um have to the internet they will actually Traverse in that Gateway and
16:08
then at that point their addresses will be netted to the internet gateway and
16:14
out to the internet the thing about the net Gateway is it actually protects these private instances because they're
16:21
not exposed to the internet the internet gateway will allow traffic through the internet gateway to access these web
16:28
services in the public subnet right right and just so you all know there's
16:33
always a joke around this but navigates cost money so just so you know they they can sometimes be a quite of an expensive
16:39
bit of your networking setup IPv6 awesome
16:48
um cool so and is this the most common use case when you see people private in public sublets would this be a very
16:54
common scenario people use yes um the private and public subnet is going to be a kind of uh um a common design
17:01
architecture because if you think about it you're going to have that clear approach to your application so you may
17:06
have a two-tier which what we're looking at you may have a three tier so you'll have let's say a API in the front
17:14
um or a low balance in the front a app layer and then um your database layer so it depends on
17:20
how you design your applications in Darko you probably can talk more about that than I can yeah yeah I mean
17:25
definitely right so especially when you're building something like a three three tier web application think about
17:31
those three tiers those also be networking fears and you don't have to expose everything to the internet that's
17:36
why you have private subnets right so if you have backend servers or servers that don't necessarily need to be accessed by
17:42
the user from the internet directly so when I say directly I mean they don't
17:47
have to hit that IP rather they go through a front-end server or a front-end service they can
17:54
be in a private IP private subnet without you having to worry about anything which is ultimately more secure
18:00
and I do think we have Brandon in the chat here who can talk to us all about securing all of these fun things as well awesome
18:08
now can we bring up a question from Napalm here about Direct Connect
18:14
I guess it's Direct Connect yes Direct Connect um can you explain when using direct
18:19
current how everything acts public to the data center network but private to the outside world this is always a bit
18:25
mind-bending to me so when you when you mention Direct
18:31
Connect and you say public you have to understand that some services live on what you call a public fifth so
18:39
like S3 those have public IP addresses they're exposed to the internet
18:44
um dynamodb that's right public right but if you look at your VPC that's going to
18:51
be private so if you need that's going to use a private event to access that bpc so some
18:56
services and that's the point of using something like a um a VPC endpoint to
19:01
kind of connect to those public services from a private subnet that so you don't
19:07
have to go Traverse the internet or through it in a Gateway you just use something like a um a VPC endpoint to
19:13
access that private service right okay awesome um just a quick comment here from fund
19:19
by KK uh what does it cost to have a VPC VPC itself is free right is that correct
19:25
yes the only couple the costs that comes to vpcs are Ingress and egress costs
19:30
that means cost of transferring data between vpcs and or uh something called
19:37
uh an app Gateway can cost you money but the VPC itself and the subnets do not cost yeah actually if Curtis you're in
19:44
the chat I actually put a link to a YouTube video that kind of
19:50
demystifies data transfer on AWS so Curtis if you could share that thank you
19:56
very much yes let me just kind of break down the different um spins that you have in a VPC
20:02
by default if you just create a VPC there's no cost for that exactly exactly and just so you know there's a limit to
20:09
five vpcs by default per region so if you need more than five apcs you need to request a service increase and that
20:16
usually breaks a lot of the stuff when I build things because I usually build a VPC with everything I build so make sure
20:21
to increase those limits as much as you need okay what we got all right so let's hop into
20:28
the AWS console and explore
20:34
all right so when we first log into AWS for those of you that don't that do not have an account aren't used to AWS or if
20:41
you are you see AWS um we're going to learn about it in the console firsthand
20:48
now the first thing we'll do is either search for VPC
20:56
and click VPC can you can you zoom in a bit just so we can see this a bit more if anybody out
21:03
there is watching on the phone so how's that look much much better thank you all right
21:09
so when we look at the VPC let's talk about some of the core components of the VPC
21:15
the first thing we have is your vpcs this is going to list all of the vpcs
21:20
that you have in that region notice here that I am a US West 2 member that I
21:27
mentioned whenever you get started with AWS you have your account which we logged into and then you select a region
21:33
here we have us West 2. now inside of the VPC or inside of that
21:41
region you have what you call your default VPC this default VPC will have a solid block
21:48
of 172.31.0.0 16. so about 65 000 IP
21:55
addresses you can actually deploy inside of this cider box
22:01
now another thing to mention is that
22:07
there's a option here that lets you know that this is the default VPC this can be
22:12
deleted and you can create it as well so every region will have a default VPC
22:20
and I'm going to name this default VPC because we'll we'll need that later in
22:26
the lab what happens if we delete the default VBS here
22:31
you can just build it you can actually get another one so okay that's cool yeah unless you have something running on it
22:38
should not break things right right it should not make great things and it's best practice to customize your VPC so
22:45
you can do them and manage them as you need to now moving on to subnets
22:52
you'll have a subnet in every availability Zone in that region that are part of the default VPC right so
23:00
here we have four availability zones so we have four subnets that are created with Slash 20s
23:07
inside of that solder block of our default VPC and notice that since I named the default VPC it now this is the
23:14
name and the VPC ID gotcha moving on to Route tables you'll have
23:21
one main route table notice this is the main route table that I mentioned every VPC you create will have a created main
23:29
route table okay and does this route table apply to all subnets uh or
23:35
by default does it apply to all subnets or do we can we have create more more route tables and assign them to
23:42
individual Summits all right so so the way this works is whenever you create a route or create a VPC that main route
23:48
table that's created every subnet that you create will be Associated by to that
23:54
or B will utilize that default route or the main route table unless you
24:01
explicitly associate it with another round table okay
24:08
and then we have our internet gateway um something else to mention in our
24:14
routes inside of that default um VPC or the the main route table
24:19
you'll have two routes this local route is for the entire side of block of that
24:24
VPC which tells the traffic or the the the VPC router how to route traffic
24:30
within that VPC okay and then you'll have a default route to in that Gateway
24:36
so any subnets that are associated with this route table are public subnets so
24:42
every subnet's within this VPC is public
24:47
and now we have our internet gateway here which is used to connect to the
24:52
internet this is attached to our default VPC
24:58
and then we have our egress Only Internet gateways which is for IPv6 and the cool thing about egress only
25:05
um internet gateway is that if you're running an IPv6 if you're using the internet gateway traffic can Traverse in
25:13
to your VPC through IPv6 but if you just want to allow traffic out since there's no Nat in ipv well that since you're not
25:21
gonna net an IPv6 address you can just utilize the egress only to only allow
25:27
traffic out of your VPC rather than in right right okay awesome I'm going to
25:32
follow you here for a second I'm just going to answer a couple of questions here we have folks coming in and chatting so
25:38
yeah by the way chat just any any questions any comments you have we can see them here and we would love to
25:44
answer them uh come here from uh F Goose money Pura asks can you explain use
25:49
cases um when to use VPC endpoints versus Gateway endpoints great question and I
25:56
love that question um so when when you're thinking about let's let's start with your VPC endpoint
26:03
let's say or Gateway endpoint that's that's the best example so if you let's
26:09
say you have an S3 bucket and you want your private instances or
26:15
your your instances inside of your VPC to access that S3 bucket the S3 bucket
26:21
at that point can use the the the instances can use the
26:27
the um Esther Gateway or the Gateway endpoint by the prefix that is added to
26:34
the route table okay and it traverses through the AWS backbone to connect
26:39
directly to S3 rather than the private or the uh VPC
26:45
endpoint that's going to be for additional Services outside of just S3
26:51
right um so and with that happened what that does is it has some DNS it uses DNS it
26:58
looks like it's inside of your subnet for that Network so you have to put one of those in each subnet okay so in
27:05
essence Gateway endpoints use route tables to access some services like S3
27:11
VPC endpoints use DNS entries to access them again all through the AWS backbone
27:16
without going to the internet but we use a different layer right and so to answer this question specifically the Gateway
27:23
endpoint is going to be for things like S3 and dynamodb and your VPC endpoint is
27:28
going to be for additional VPC Services okay that you want to provide private
27:34
access awesome awesome um before we move on a couple more questions coming in from Fun by KK
27:39
having the option to build multiple route tables was confusing to them can I suddenly have more than one route table
27:45
and can a subject have no relative tables no and no no and no
27:52
simple as that yes if a subnet is not associated with the route table it will
27:57
utilize the main route table for that VPC yeah and as well as when it comes to
28:03
having multiple route tables you have to think about the reasons for having multiple route tables one of the reasons
28:09
could be segmentation if you have a route table that has a route to the internet gateway at that
28:17
point traffic can come into your network in Access devices now of course you can
28:23
use security groups and things like that to prevent that but if you have at that internet gateway attached that subnet is
28:29
a public subnet now if you join to prevent the external access what you could do is create
28:36
another route table and then associate this private subnet so the subnets to
28:41
that route table and then since they don't have a route to the internet gateway their private supplements and so
28:47
at that point you can add a route to and that Gateway or something like that great great awesome uh we have more
28:52
questions from The Tech Guy 21 but we're going to get to those in a second so please stay on while we move on with
28:58
some other VPC basics okay um let's see I was at the egress
29:05
yeah yeah six I think that's all oh the oh the last
29:10
thing would be peering connections yes so what is VPC appearing that's that's a term that's being thrown around left and
29:16
right and why what is it and why should we use it that's a great question what is it enables you to Route traffic via
29:24
private IP addresses between two peer vpcs so
29:29
go ahead.com no no yes I'm saying yes I want to continue explain it to me yes so
29:36
I mentioned that we have the concept of private subnets and if you want those probably something that's to communicate
29:41
with each other or if you need to communicate with another VPC you can establish a pre-ordering connection
29:47
which is a one-to-one connection between vpcs now that Parent Connection isn't going to be transitive so you can't
29:53
um route that Parent Connection to another VPC you have to use something like Transit Gateway for that but if you need to like share services from a
30:00
single VPC to other vpcs you could pair the other vpcs to that single VPC and
30:06
now you have like a shared services peer connection yeah yeah so in essence subnets from private subnets from two
30:13
different vpcs cannot communicate with each other unless you have EPC peering enabled and we'll demonstrate that so
30:19
you can okay go for it all right so before we actually get to
30:25
the VPC pair let's launch an ec2 instance you like ice cream
30:31
I love ice cream Dawn okay tell me more about this ice cream yes let's build a
30:37
web server that serves ice cream here on AWS okay
30:42
all right that's all for that all right so the first thing we'll do we'll we'll go to ec2 instances
30:48
uh we'll click running there's no running instances in ec2 console and we'll create a launch
30:55
instance foreign server
31:01
that sounds that sounds good I will make this Amazon Linux 2. Amazon
31:09
Linux we'll use the defaults in the free tier so for those of you that aren't
31:14
don't know about the free tier Curtis if you could post a link to the free 10 in the chat yep
31:21
in the free tier basically lets you know what services um are free up to a certain point or
31:27
just are always free on AWS so make sure you check out that link so you know what
31:33
resources you can spend up without being having spent we're not going to use a keyboard key
31:39
pair because we're going to connect to this device through SSM and I'll show you that here in a moment
31:45
we'll click edit under network settings because I want to make sure that I click the right subnet which I could since
31:52
we're using the default VPC for this um I can actually use any subnet but I'll go ahead and take the first
31:58
available and notice that it says default VPC so that's why I named it so we can clearly
32:04
see that this is the default VPC right did you did you choose something which is public or private in this case it all
32:11
of a sudden that's in the default VPC are public okay they're all public okay so they're all internet facing yes okay
32:17
we need to ensure that we get Auto assigned at ipv4 address okay so we'll
32:23
click that and what we could do here is create a
32:28
security group so we'll name the security group and we'll call this um ice cream SG
32:38
and now we're going to make sure that we can access this via
32:45
HTTP okay and we'll do it from anywhere so if
32:51
someone wants to access it they can and now one more thing I want to do so
32:57
we can connect test connectivity we're going to use what you call an instant profile which is basically an IAM role
33:03
that says that SSM will allow will give us privilege to be able to access this device from our AWS console yep okay
33:12
so basically this by default ec2 instances have a systems manager agent running on them ec2 instances running
33:19
Amazon Linux has a systems manager agent running on them so we can access them through that service it's a service that
33:24
shows up on the show all the time it is just a fantastic thing yes it is it is
33:31
um so we'll click create in-store launch instance and at this point our instance is spinning up okay now
33:38
I mean I mean I know what you're right I forgot the ice cream we got the ice
33:45
cream got the ice cream so we'll terminate this instance because I didn't give it ice cream
33:50
so we'll go back and we'll launch another instance yes see ice cream service that's the beauty of the cloud you can
33:57
you can you can you can make a mistake and you say like you know what let me do that again and it works immediately I
34:03
love that all right so we go through the same things same thing it's just I created a group I'll click click that same group
34:09
and we're just spinning through this extremely fast because I did all the things before so my security group was
34:16
already created from that last sentence and the next thing we'll do is we'll add user data to launch our server awesome
34:24
while Duane is doing that user data is a script in this case A bash script that runs during the execution during the
34:31
first launch of the server and it executes a bunch of commands and I guess that they're gonna set up this server to
34:38
be an ice cream server in some way shape or form so uh yeah it's a wonderful way
34:43
to kind of quickly set up newly booting servers so there you go it's a yes it's
34:49
a thing so basically I have a repo here that is going to clone that repo it's going to start spin up a download and
34:56
install Apache it's going to start that server and then it's going to copy over my HTML files to the folder and then
35:03
it's going to get the public IP address region and we'll see all that on the screen
35:09
okay logic instance launching instance now the system should be sitting in a VPC in a public subnet with a public IP
35:17
so in essence we should be able to access it once it boots up we should be able to access it using the using its
35:22
public IP right yes we should so it's it ha it's not in a run estate
35:28
so if we remove running you will see this is actually an independent site
35:33
eventual consistency so it's going to come up online okay do you want what we're waiting for that there's there's a
35:39
comment here from The Tech Guy 21. it's kind of an off topic but I would say it's still on topic um any good material on any cast how any
35:46
cast is used by global accelerator to broadcast that static IP to the routers uh how does the client find the nearest
35:53
Edge location hosting the static IP this is about the AWS Global accelerator
35:59
I can find a blog or something yeah so John has done some content regarding the
36:05
global accelerator for all of you who do not know Global server there is a service that basically accelerates somewhere traffic by making
36:12
endpoints or static IPS available closer to the um to the location basically moving them
36:18
to the Edge Edge instead of traversing multiple different uh isps to get to the
36:24
server on on AWS you enter the enter the AWS backbone through an edge device
36:30
via a static IP so that's kind of how it works uh well that's what it does how it
36:37
works I have no idea like when we get to the scale this is already insane I
36:42
actually just gave Curtis a Blog so Curtis if you could share that blog in the chat and and The Tech Guy 21 if you
36:49
check it check out take a look at that blog that should answer all the questions that you had okay
36:55
so and by the way we are uh just so you know we are live tweeting every session we do on on Twitter so if you head out
37:03
over to aws.twitter.com AWS developers you will see
37:08
uh live tweeting sessions for every stream we do including this one and you'll find a bunch of links and
37:14
comments there as well so okay we should instance running yes our
37:19
instance is running um it's initializing so we need to kind of wait on that but while we're waiting let's um actually create a VPC
37:30
so we'll open the VPC console
37:35
and the cool thing about this console what I I really like about it you'll see in a moment is that we have the option
37:41
to create a VPC okay we have the option to create subnets
37:48
we have the option to create route tables I think you kind of get my point but if you go if you go to the VPC
37:54
dashboard if you're just getting started with AWS you can use the click the create VPC
38:01
um icon and then once you click that that download box what happens is you
38:07
actually get a preview of everything that you're going to build on AWS yep and so that is beautiful yes I actually
38:13
love that so we can call this build on we'll call this to build on VPC
38:20
VPC
38:26
[Laughter] and we'll we'll use the defaults for The
38:32
Cider block and we'll do ipv4 okay for that I'm going to use IPv6 will keep you
38:39
simple um the Tennessee will leave a default that means that basically our VPC is
38:45
going to span multiple servers if we wanted to use um the actual dedicated our VPC will
38:51
live on specific Hardware yep now we'll just use one availability Zone
38:58
here but if you wanted to use two or three notice how it spins up subnets
39:03
private and public inside of our PPC that is actually quite useful I think
39:09
like you know just having the visual uh visual representation of what you're going to build is is pretty pretty cool
39:15
right for sure yeah yeah Alex Alex the question this is the create new VPC view
39:21
this is something that's relatively newish but it's just fantastic so if you go to the VPC console and click the Big
39:26
Orange button create new VPC you get this yes it's a few months old when they first
39:33
yeah I was like wow okay this makes it so simple to walk through totally totally we have our public private
39:40
supplements um if we want to use in that Gateway we could um I'll go ahead and use one that Gateway
39:48
since we're using one subnet so you all could see and here's the option to create ns3 endpoint or Gateway endpoint
39:55
but we won't create that okay and then we enable DNS host names and DNS resolution the host Angel resolution
40:03
resolution allows us to resolve a public IP address a DNS name to our public IP
40:10
address as well as a private uh DNS name inside of our vpcs
40:15
um subnets and notice that if we look at the flow
40:21
chart we're creating a VPC with two subnets each subnet is attached to its own route
40:27
table correct something with this on Route table and then it lets you know the kind of traffic the way traffic
40:34
traverses that route table so this route table will send traffic to the internet gateway
40:40
and this route table will send traffic to the net Gateway in order to reach the internet
40:46
okay and now we'll click create VPC I think all of these things now one one
40:54
new thing about vpcs is that when you create them creates all of these things that's that's not new but when you
41:00
delete them when you delete the VPC it deletes all the things together I believe in the past you have to do it
41:06
manually you have to delete all the subnets manually or something but now it deletes everything for you which is
41:12
which is just wonderful you may run into some challenges um like if you have instances inside of
41:18
a subnet or something of course so you have to delete the resources first for that to happen but it'll tell you
41:23
actually what's going on yeah yeah in the past you had to kind of find out yourself and it was it was a whole mess
41:29
I I recall it was it's way easier to clean up now than it used to be before yes
41:35
now let's open the ec2 console we'll open it in a new tab and our ice cream
41:42
servers should be done um building okay notice that we have the
41:47
two by two checks if we click the check box beside it notice that we have a
41:53
public IP address we have a private IP address for our subnet
41:59
and then we have public DNS name for our instance
42:05
let's look at some ice cream what's your favorite ice cream Taco uh anything to do with chocolate I would say so
42:11
anything to do with chocolate let's see yeah if we go to our ice cream server let's
42:18
see if it's up and running there it is the world all right first ice cream list yeah
42:24
okay and it tells us the actual IP address of our instance so if you notice
42:31
that's the IP address that we use to connect to this device yeah let's just know the region that we built it in
42:37
and then if we can find chocolate that's number 13 on the list
42:52
okay okay well I'm not sure I agree with this list but hey you know it's the internet we all have opinions
42:59
[Laughter] um so our VPC should be done building
43:06
with all the things and notice that it's for the created if
43:12
we go back to the your VPC section of the VPC console notice that we have the
43:17
ball doing VPC and the default VPC okay
43:23
now I want to launch an instance in the Bardon VPC and then I want to connect
43:29
these two to see if we can get connectivity okay so we'll create a bottle instance
43:39
so well well Juan is creating this uh just want to answer a question that has been uh uh up in the chat somewhere uh
43:47
yeah gurus writer is commenting on is private is there private IP conflicts when doing VPC peering yes that can
43:54
happen this is where you have to take into account having different ranges in different vpcs because if you connect
44:00
them and you have the same IP ranges that there may be a problem so yeah don't do
44:06
that and I and I figured I would get this question so yeah darker I'm going to send you a link send me a link yes
44:14
this link is for what how to handle overlapping IP
44:20
addresses okay Mr Guru Swagger here's the link for you
44:25
in the chat you can check it out how to handle um overlapping IP ranges on on VPC
44:35
okay so we're doing very similar however Duan is launching an instance in
44:41
the other VPC so it's not going to exist in the same VPC as the one before is it
44:46
going into a private Subnet in this case yes this is going to go go into a private subnet okay
44:52
all right and so now I'm creating the security group [Music]
44:58
I removed this rule we won't add any rules we'll just create Security Group see
45:03
what happens and then we'll add our instance profile okay so we can access it through
45:09
assistance manager right yes yes
45:15
okay so now this instance is sending in a in a private Subnet in essence you
45:21
cannot access this instance there's no public IP address on this instance um you we can access it through systems
45:27
manager and that's all and that's all so if we I want to connect to the ice cream server
45:34
assistant manager right so we'll click connect and then we'll connect
45:44
this is one of the great things that I like about systems manager is it allows us to
45:49
connect directly to it from let's see is I don't can answer your answer so I think you you use the instance connect
45:55
so go back and uh go to the session manager
46:01
should have let me troubleshoot it we only have 12 minutes left about 12
46:10
minutes 12 minutes not enough but we are connected now we are boom we are
46:15
connected let's verify IP address all right
46:27
all right let's see if this instance is still initializing all right so for the
46:35
sake of time we have about 12 minutes but tell me what you're trying to do like I think it should be it should be it should pick up while you tell me
46:41
explain to me what we are trying to do right now all right so what we have done so far is we launched a server into the
46:50
um default VPC okay and then we launched another instance into a newly created
46:55
VPC what I want to do is establish connectivity or verify or even see if we
47:00
have connectivity in between the two vpcs so once this instance is run up and running what we'll try to do is Ping in
47:07
between the two and see if we have connectivity to see how private a VPC actually is okay but you want to connect
47:14
through oh okay so are you gonna do some VPC peering or yeah okay yes the goal is the
47:20
VPC pin so okay that's the end one okay maybe maybe we can try to connect
47:26
sometimes it's just eventual consistency so just try to maybe run a session manager on it already so let's let's see
47:32
if if it's ready for us is it ready it's ready there you go
47:39
so let's see our private IP address of this device notice that it's inside of the subnet or
47:47
The Cider block that we created for the new VPC okay so let's see if we can pin this IP address from our instance
47:57
so I'll be paying from the ice cream server to the build on instance yep
48:05
doesn't work doesn't work yep okay
48:12
and if we go to have the direction it doesn't work of
48:19
course for the second time of course some people may say well is there a rod on the right table so we
48:26
check the two routing tables that we have for the barn on private
48:31
there is not a route which that could be a reason so but
48:37
there is a route to a net Gateway correct so what does that mean well if
48:43
we go back to the instances and we look at the ice cream servers public IP address let's see if we can payment
48:50
on the ice cream server server right
49:01
are we paying that it could be just because of the icmp doesn't go through right the icmp
49:07
protocol just doesn't work through a ping but in essence you should be able to connect to it uh maybe using curl or something so
49:16
yeah all right we got the two by two checks so what we'll do is establish connectivity between the two
49:24
by the way to answer the question in the chat coming in from from Matt had 91 can
49:31
can only employees of Amazon present on this channel well this is the Channel owned by the folks at or at the US and
49:37
uh technically yes but we get guests and and the community members and people from all over the world to join us on
49:44
streams but uh we do run the shows right and you mentioned a good point I didn't
49:49
allow icmp through the security group so we would have to go back and add that okay but we'll do that as well
49:55
um so with the parent connection let's go ahead and establish that because I think we got what eight minutes yep so
50:01
what we'll do is we'll enter back into the VPC console we'll clip pairing we'll click create peering connection
50:07
and we'll call this ice cream pair
50:18
and will establish the appearing connection from our default VPC
50:23
now since I own both of these I'll just be the requester the one that's requesting the connection and then the
50:30
acceptor is going to be the Baltimore VPC yep you have the option to use our
50:35
account or a different account and we also can use another region within our account okay at that point we just click create
50:43
peer connection and then now we have to accept the peer
50:49
and so once we accept that parent request if we go back into parent connections we
50:56
should see that our parent connection is active right okay
51:01
and we're good now we still can't we still don't have connectivity there's a couple things we need to do the next
51:07
thing we need to do is add a route to each subnet so we'll go into our private route table
51:13
and we're at a route pointing to the default VPC
51:21
okay the peer and we'll use VPC pair for that
51:29
and we'll use our parent connection to be able to connect to okay so basically what we're saying here
51:36
if any client ends up in this subnet is trying to reach an IP address in that range it will go over through the over
51:42
through that VPC period of connection correct correct and now we'll go back to round tables
51:47
one more time and then we'll find our default bald on Round Table that's
51:55
has our is it that one is it the other one it's
52:01
the default it's the default one there we go what's the default so in a route for the VPC we just created
52:09
slash 16 it will point to the ice cream pair
52:15
and now we establish that connection so also we have a route the next thing we
52:20
do need to do is since security groups is like a stateful firewall we need to add a
52:26
a rule that allows traffic into the uh
52:32
Bardon Security Group [Music]
52:38
and so here is where we'll allow icmp okay
52:50
and the source is going to be uh 172 the default
52:58
yeah 16. okay let's say the rule and so no
53:04
now at this point for the broad on security group we should be able to access that
53:09
that's right let's try
53:18
so you will see people who are network admins they recognize their servers based on IP addresses like Duan here I
53:24
would probably set up a hostname or something but do on here just goes ifconfig if that's all he needs
53:32
actually we already had the pain running still we still had to paint running so we have connectivity between the two
53:37
vpcs amazing look at that yeah beautiful let's see beautiful five
53:43
minutes to spare five minutes to spare there you go I mean so you know
53:49
this is very important understanding that that what are vpcs is kind of a basic thing and you we all kind of brush
53:55
it off like oh yeah that's just exists but vpcs are your network segments your data centers per se if you would like to
54:02
call them that way where you put your subnets and and gateways and Route tables and all that fun stuff and you
54:08
can use different route tables you can connect different vpcs together as you've seen here and you should also
54:14
definitely not put everything in a public subnet so if you're building ec2 instances if you're building uh things
54:19
within a VPC make sure to use the appropriate subnet configuration be that the private
54:27
or a public one um awesome we do have a couple of comments here regarding your ice cream
54:32
uh it seems the chocolate is number 13 because of alphabetical sorting so um I
54:38
would uh I would I would deduce it that it's number one um
54:44
there's a comment here again from The Tech Guy 21. welcome back does Route 53 name servers also use
54:51
anycast IPS uh what happens when I access from East Coast versus someone asking from Australia I guess it's it's
54:57
it's it's related to the global accelerator um you can control you can control that
55:03
too um yeah awesome uh so Dobson uh the the the
55:09
the where you can watch this is you can also watch it here on on uh on Twitch as
55:14
soon as we're done you're going to be able to watch this again but there is a better option for all of you wonderful
55:21
people out there the build on AWS YouTube channel go there smash the like And subscribe
55:27
buttons or whatever you could say these days and um all the recordings of previous streams are there so you should
55:32
be able to check those things out um a bunch of questions coming in uh
55:40
Ricardo asks if a VPC can communicate with another VPC through peering is it okay to mix chocolate ice cream with
55:46
bacon yes it's been done it's been done it's been
55:52
done absolutely um amazing so so let's let's actually slowly wrap up this thing because
55:58
there's a couple of minutes left and by wrap up I mean I want to ask something to the wonderful audience here hello
56:03
Chad hi um in the chat thing you will see a survey now we love doing this show every
56:11
week and it's been wonderful 16 episodes so far getting amazing guests people like Duan we're missing Jackie today
56:18
unfortunately she's all the way in San Francisco doing her own live stream without me and
56:23
um but I do want to hear your opinions um let us know did you like this episode
56:29
did you like the show is this something you enjoy would you watch it in the future and most importantly tell us what
56:37
topics what content what guests would you love to see in the future so the link there in the chat is posting it
56:44
again please please for my own sake tell us what you
56:49
what you think we based off a lot of the content on your feedback we got a lot of feedback we want security content we had
56:55
a security episode with Brandon there was con Community comments on day one network content here we go we have Duan
57:01
here so uh please do let us know in the future um awesome uh have me on the show manager
57:08
from Capital One I mean Mad Hat if you can talk and build stuff I mean Hey listen
57:13
um we'll have anybody here who wants to talk about some cool technology that that can be useful to The Wider
57:20
developer audience um Dawn any parting thoughts
57:26
party thoughts yes thank you for having me on build be a
57:31
Baldwin AWS today called on AWS absolutely absolutely
57:39
I think Curtis has a ton of links to help you learn about Amazon Network or
57:45
AWS networking and to get started with AWS networking if you all have questions
57:50
please feel free to reach out to me I had a great time you know building what you are and I look forward to joining
57:57
everyone again thank you thank you everyone thank you so much this has been a wonderful thing please do stay tuned
58:04
on the twitch.tv Channel there may be more shows coming up after hours so thank you all for joining see you all
58:09
next week same place at the same time we're having somebody from O'Reilly some master in Python language teaching me
58:16
how to write the python application so next week same place same time watch Darko stumble while he tries to write
58:22
something in Python so once again Juwan thank you so much it's Bill pleasure
58:29
hey there thanks for checking out this video remember to give it a like and share with your community then hit
58:35
subscribe and the bell for all the latest content that will help you build on AWS

