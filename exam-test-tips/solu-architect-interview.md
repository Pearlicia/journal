### (Master the Solutions Architect Interview Questions on the Technical Interview!)

Are you looking to excel in your next cloud architect technical interview? If so, this blog is for you. Today, we give you five cloud architect, or solution architect interview question.

At Go Cloud Careers, we spend a lot of time teaching you how to interview. What we’re looking for is do you know the materials, and can you communicate those materials? Focus on your communication and delivery at least as much as your technology knowledge! If you know it, but can’t explain it, the hiring manager might not see your competency.

### Question 1. “When connecting to AWS, when would you use a direct connection and when would you use a VPN?”
With this question, we can figure out if you know the differences, architecturally speaking, and in particular the strengths and weaknesses of each approach.

“An architect would know to use the direct connection when there is a need for guaranteed bandwidth, latency, and performance. With a direct connection, there are some things that happen along the way, but it’s effectively like you have a wire between two different locations. The latency on the wire (how long it takes to go from both ends of the wire) doesn’t change. Thus, if you’ve got a 10-gigabit link, you’re going to always have 10 gigabits.

Simply put: the latency, performance, and bandwidth are consistent.

With a VPN, you connect to the internet on both sides, then you create a tunnel and encrypt your data over the internet. The internet is not private and that’s why you have to encrypt your data. The advantages when you use a VPN are that it’s typically cheaper because you’re not buying a direct connection from two different locations; you’re just connecting to the internet. Also, VPNs are simple to set up because you can create any connection to any place that has internet connectivity.

The disadvantage with a VPN is that internet bandwidth, latency, and performance are not guaranteed. Your internet service provider may guarantee you access to them, but once you get off their network and on the internet, there are no guarantees. Internet is basically best-effort delivery. In simple terms, if I try to reach a webpage, it doesn’t mean it’s going to get there. It should and It’ll try, but it’s not guaranteed. Performance on the internet can be all good, perfect, or horrible. Over a wire, if it takes 3 milliseconds, it’s always going to do that. When you’re dealing with the internet, because your speed is not guaranteed, your performance and your latency is not guaranteed either. You can run into variations in latency (called “jitter“). For example, if the first message takes 2 milliseconds, the second 100 milliseconds, and the third 5 milliseconds – message 2 is going to arrive long after message 3 and that may be a problem.”


### Question 2. “What is BGP and why is it used?”
“BGP, or Border Gateway Protocol, is an exterior gateway protocol. It is a path vector protocol that operates on TCP port 179. You use exterior gateway protocols when you connect an entity to an external entity. That’s why organizations use BGP to connect to AWS or GCP.

BGP is highly tunable and highly scalable. For example, an internet routing table has three-quarters of a million routes. BGP can easily handle that, whereas an interior gateway protocol could not. Interior gateway protocols for example, OSPF and EIGRP.”

### Question 3. “You are designing a video streaming solution on the cloud and the application developers don’t know whether you should use TCP or UDP. Which should they choose and why?”

The reason you got to ask this kind of cloud architect question is the cloud architect is an adviser. They’re a business strategist and they’re a designer. A hiring manager really wants to know if you understand what TCP is and UDP is.

“If you’re designing a video streaming solution, it must be UDP, not TCP! UDP is used for real-time streaming, which means voice or video, it must be UDP. You use UDP for real-time applications. UDP is better, and faster for these applications. There are no sliding windows. Performance is going to be what it’s going to be. Also, there’s no re-transmission of lost data.

Why can’t you use TCP for streaming? TCP is used for reliable transfer. Let’s say I had a sentence, “Mike likes BGP.” That’s the sentence. If I send it via UDP and the message was “Mike BGP,” that’s fine because it lost the word “likes”. Now, it’s preferable if it comes out as, “Mike likes BGP.” But if it just is “Mike” and “BGP”, that’s fine.

By comparison, if the message was delivered out of order because TCP re-transmits the data. What if it says, “Like BGP Mike,” because Mike came out of order? That’s what could happen on TCP with re-transmissions.”

### Question 4. “What is CxO relevancy? What does it mean to present differently to a CxO versus an engineer?”

This is a behavioral presentation kind of question that is asked very frequently.

“A CxO is a C-level executive. When you present to the CxO, your presentation must be very different than a presentation to an engineer. For the most part, they’re not technical people. Even at the CIO level, they’re executives. Executives are extremely busy people. That is why they’re going to have an attention span of a few seconds at max. You must get your concept to the executive quickly and to the point. Also, you must talk about things that they care about.

The Chief Executive Officer, or CEO, is tasked with the organization’s strategy and increasing shareholder value, and improving their performance, meaning revenue or profitability growth. They care about that. When you present tech to the CEO, you must show that’s what’s going to happen.

The Chief Financial Officer, or CFO is the gatekeeper of the organization’s finances. They care about that. When you’re presenting to the CFO, you should be really good at doing some ROI modeling and showing that the value provided by your solution, provides greater value and savings or profitability to the company than it’s cost.

The Chief Information Officer, or CIO needs to know that your technology solution is going to

meet the CEO’s goals and needs. You’ve got to present this and that it’s going to work.

Engineers might need a lot of depth. You must present the right message to the right audience at the right time. As an architect, you’re going to be with executives and with engineers. You must be able to speak all the languages.”

### Question 5. “How do your background and experience prepare you to be a solution architect?”

The question is very common and gets really tricky, it’s another behavioral question.

First and foremost, you need to understand the solutions architect role. The solutions architect is a type of architect. They’re the system designer. That means they are not a SysOp or DevOp person, nor a programmer.

What does prepare you to be an architect? Communication and presentation skills, and knowledge of all the systems you’re going to be interacting with, which is the network and the data center. So if someone asks you the above question – Tie those things in.

For Example – My background and experience helped me to be a great architect because I worked in sales for several years. I learned how to communicate and consult with executives. How to consult with clients, ask about their needs and design a solution that would work for them and persuade them that it was the right solution. In addition, I spent a lot of time in networking, which is the foundation of the cloud. That helps prepare me. I’ve spent time learning about cloud computing, about the AWS, the GCP services. I also have an extreme security background and I’m a CISSP. Thus I know how to design the network and the security systems. I how to communicate with executives.

You’ve got to show them the background of the experience that matters. When you’re preparing for a solution architect, talk about the things that matter. Your soft skills, your emotional intelligence, your presentation skills, your design skills, and your knowledge of the network of the data center. Those are things they’re going to close it for you. Those are things you go for the win. You must show the hiring manager that you’re the right person for the job. And then your background and experience can make their life better.

### Conclusion
You want to show the hiring manager that you have the technical competency to perform the job by answering these types of questions in a way that proves that you understand the strengths and the weaknesses of each technology and why you would use them.

Because what does an architect do? They design a solution to solve a customer challenge. And you have to understand the technology in order to design solutions. Be able to tell the hiring manager about any technology they ask you in the following manner. What is the technology, how does the technology work, and why you would use it.

Do this, and you will prove to the hiring manager that you’re in the top 10th of 1% and you will be hired, and you will get paid more and you will have a wonderful cloud computing career.





