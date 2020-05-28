Internet Protocols Demystified
Mar 11, 2020

Protocols sound scary and complicated. But while the details of protocols themselves are complicated, they exist to make other things simpler. Let’s investigate protocols with some everyday examples, and a command line exercise.

What is a protocol?

What’s the first thing you think when you hear the word “protocol”? Maybe “diplomatic”? Diplomats specialize in making agreement and transfers across borders. To do that, you need a protocol: a set of behaviors to agree on.

In a web page, separate parts of the code are responsible for separate jobs. HTML, CSS and JavaScript all have specific jobs; but before they can do their jobs, they have to get to your computer. Getting there is the job of the Hypertext and Internet Protocol Suites.

Real World Example

These protocol suites are a group of behaviors that clients and servers agree on to make transfers. Your browser handles several of these for you. Let’s look at the most important four:

URL > DNS > IP > HTTP

That Senator said the internet is a series of tubes, but the internet is like the old-timey telephone system.

The URL is like the caller stating who they’d like to talk to. The browser reacts like a telephone operator, and starts the process of connection by looking up the name of the callee.

DNS is the Domain Name Service, which functions like a telephone book, translating the alphanumeric domain name into an IP address.

The IP in ‘IP Address’ stands for Internet Protocol. IP is responsible for the intermediate communication between the parties. In the phone analogy, IP is equivalent to normal conventions of speaking on the phone — for example, if one party doesn’t hear the other for a particularly long time, or if there’s noise on the line, they check if the other is still receiving.

Hyper Text Transfer Protocol covers the conventions of a conversation. Both parties start by saying hello, and agreeing on a language. The request may specify how the answer will be formatted, the response may demand the user identify themselves or limit what they can ask.

Exercise

Start by opening a terminal. On Mac or Linux you have one built in; on Windows I highly recommend (Git Bash) [https://gitforwindows.org/].

The `nslookup` utility allows us to interact with the DNS protocol. Give `nslookup` a domain name, and it will return the associated IP address:

$ nslookup google.com
Server: 209.18.47.61
Address: 209.18.47.61#53Non-authoritative answer:
Name: google.com
Address: 216.58.192.174

The first “server” and “address” represent where `nslookup` got its information from (in our telephone analogy, which telephone book got used). The ‘address’ in the answer is the IP we can expect to find the domain at (“non-authoritative” means your local DNS server is not in charge of this domain, and got this information from some other DNS server).

Now take that IP address, and paste it into the address bar of the browser. You should get the Google home page, because the browser knows how to look up IPs as well as domain names (this doesn’t always work — sometimes the IP is an intermediate machine, like a load balancer).

Speaking of intermediate machines, let’s look at how IP directs our traffic by using `traceroute`:

$ traceroute 216.58.192.174
traceroute to 216.58.192.174 (216.58.192.174), 64 hops max, 52 byte packets
 1 192.168.0.1 (192.168.0.1) 2.308 ms 1.556 ms 1.368 ms
 2 142.254.209.133 (142.254.209.133) 12.264 ms 12.465 ms 13.588 ms
 3 agg63.scbome0802h.northeast.rr.com (24.58.224.229) 33.023 ms 23.830 ms 23.815 ms

Each “hop” is the “packet” of information being passed from one intermediate machine to another. Notice the final hop ends at the IP which DNS gave us. If you ever find a situation where someone is getting a totally different response than you, `traceroute` helps to check if it’s because their network is routing the request differently.

What happens next?
Once the URL > DNS > IP chain reaches its final destination, then HTTP can start its job. In an upcoming lesson, we’ll explore HTTP in depth.
