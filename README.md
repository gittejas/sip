sip
===
Session Initiation Protocol

3.1 Introduction to SIP (Session Initiation Protocol):
               The Session Initiation Protocol (SIP) is a signaling protocol for initiating, managing and terminating voice and video sessions across packet networks. SIP sessions involve one or more participants and can use unicast or multicast communication. Borrowing from ubiquitous Internet protocols, such as HTTP and SMTP, SIP is text-encoded and highly extensible. SIP may be extended to accommodate features and services such as call control services, mobility, interoperability with existing telephony systems, and more. [4]
Session Initiation Protocol (SIP) is an application-layer control (signaling) protocol for creating, modifying, and terminating sessions with one or more participants.
These sessions include Internet telephone calls, multimedia distribution, and multimedia conferences. SIP invitations used to create sessions carry session description that allows participants to agree on a set of compatible media types. SIP makes use of elements called proxy servers to help route requests to the user's current location, authenticate and authorize users for services, implement provider call-routing policies, and provide features to users.  SIP also provides a registration function that allows users to upload their current locations for use by proxy servers.  SIP runs on top of several different transport protocols. [3]
SIP is being developed by the SIP Working Group, within the Internet Engineering Task Force (IETF). The protocol is published as IETF RFC 2543 and currently has the status of a proposed standard. The latest version in SIP is Version 2, released in March 1999. [5]

3.2 RFC 3261:  
          In computer network engineering, a Request for Comments (RFC) is a memorandum published by the Internet Engineering Task Force (IETF) describing methods, behaviors, research, or innovations applicable to the working of the Internet and Internet-connected systems. The inception of the RFC format occurred in 1969 as part of the seminal ARPANET project. Today, it is the official publication channel for the Internet Engineering Task Force (IETF), the Internet Architecture Board (IAB), and—to some extent—the global community of computer network researchers in general.
Through the Internet Society, engineers and computer scientists may publish discourse in the form of an RFC, either for peer review or simply to convey new concepts, information, or (occasionally) engineering humor. The IETF adopts some of the proposals published as RFCs as Internet standards. RFC 3261 is for SIP. [9]
        SIP supports five facets of establishing and terminating multimedia communications:
User location: determination of the end system to be used for communication;
User availability: determination of the willingness of the called party to engage in communications;
User capabilities: determination of the media and media parameters to be used;
Session setup: “ringing”, establishment of session parameters at both called and calling party;
Session management: including transfer and termination of sessions, modifying session parameters, and invoking services.
          The nature of the services provided make security particularly important. To that end, SIP provides a suite of security services, which include denial-of-service prevention, authentication (both user to user and proxy to user), integrity protection, and encryption and privacy services. [8]
SIP was originally designed by Henning Schulzrinne and Mark Handley starting in 1996. The latest version of the specification is RFC 3261 from the IETF SIP Working Group. In November 2000, SIP was accepted as a 3GPP (3rd Generation Partnership Project) signaling protocol and permanent element of the IMS (IP Multimedia Subsystems) architecture for IP-based streaming multimedia services in cellular systems. 3GPP is a collaboration between groups of telecommunications associations, to make a globally applicable third generation (3G) mobile phone system specification within the scope of the International Mobile Telecommunications-2000 project of the International Telecommunication Union (ITU). 3GPP specifications are based on evolved Global System for Mobile Communications (GSM) specifications. 3GPP standardization encompasses Radio, Core Network and Service architecture. [8]
3.3 Structure of SIP protocol:
      SIP is structured as a layered protocol, which means that its behavior is described in terms of a set of fairly independent processing stages with only a loose coupling between each stage. The lowest layer of SIP is its syntax and encoding.  Its encoding is specified using an augmented Backus-Naur Form grammar (BNF). The SIP protocol is situated at the session layer in the OSI model, and at the application layer in the TCP/IP model. SIP is designed to be independent of the underlying transport layer; it can run on TCP, UDP, or SCTP. SIP works with both IPv4 and IPv6. [12]
The second layer is the transport layer.  It defines how a client sends requests and receives responses and how a server receives requests and sends responses over the network.  All SIP elements contain a transport layer.  
   
Transaction
User

Transaction
Layer

Transport
Layer

Syntax & Encoding

                                       Fig 3.1: SIP Stack Structure      

         The third layer is the transaction layer.  Transactions are a fundamental component of SIP.  A transaction is a request sent by a client transaction (using the transport layer) to a server transaction, along with all responses to that request sent from the server transaction back to the client.  The transaction layer handles application-layer retransmissions, matching of responses to requests, and application-layer timeouts. The transaction layer has a client component (referred to as a client transaction) and a server component (referred to as a server transaction), each of which are represented by a finite state machine that is constructed to process a particular request.
 The layer above the transaction layer is called the transaction user (TU). When a TU wishes to send a request, it creates a client transaction instance and passes it the request along with the destination IP address, port, and transport to which to send the request.  A TU that creates a client transaction can also cancel it. When a client cancels a transaction, it requests that the server stop further processing, revert to the state that existed before the transaction was initiated, and generate a specific error response to that transaction.  This is done with a CANCEL request, which constitutes its own transaction, but references the transaction to be cancelled. [12]
       
            SIP Dialog: Certain other requests are sent within a dialog.  A dialog is a peer-to-peer SIP relationship between two user agents that persists for some time.  The dialog facilitates sequencing of messages and proper routing of requests between the user agents.  The INVITE method is the only way defined in this specification to establish a dialog. INVITE method is used to establish a session between participants.  A session is a collection of participants, and streams of media between them, for the purposes of communication. [11]

3.4 SIP Entities:
                SIP clients typically use TCP or UDP (typically on port 5060 and/or 5061) to connect to SIP servers and other SIP endpoints. SIP is primarily used in setting up and tearing down voice or video calls. A SIP network is composed of four types of logical SIP entities. Each entity has specific functions and participates in SIP communication as a client (initiates requests), as a server (responds to requests), or as both. One physical device can have the functionality of more than one logical SIP entity. [6] For example, a network server working as a Proxy server can also function as a Registrar at the same time.


         Following are the four types of logical SIP entities:

1. User Agent: In SIP, a User Agent (UA) is the endpoint entity. User Agents initiate and terminate sessions by exchanging requests and responses. RFC 2543 defines the User Agent as an application, which contains both a User Agent client and User Agent server. 
             User Agent Client (UAC) —a client application that initiates SIP requests
             User Agent Server (UAS) —a server application that contacts the user when a SIP request is received and that returns a response on behalf of the user.
Some of the devices that can have a UA function in a SIP network are workstations, IP-phones, telephony gateways; call agents, automated answering services.

2. Proxy Server:  A Proxy Server is an intermediary entity that acts as both a server and a client for the purpose of making requests on behalf of other clients. Requests are serviced either internally or by passing them on, possibly after translation, to other servers. A Proxy interprets, and, if necessary, rewrites a request message before forwarding it.

3. Redirect Server: A Redirect Server is a server that accepts a SIP request, maps the SIP address of the called party into zero (if there is no known address) or more new addresses and returns them to the client. Unlike Proxy servers, Redirect Servers do not pass the request on to other servers.

4. Registrar Server: A Registrar is a server that accepts REGISTER requests for the purpose of updating a location database with the contact information of the user specified in the request.

3.5 SIP Messages: 
A SIP message is either a request from a client to a server, or a   response from a server to a client. There are two types of SIP messages:
Requests—sent from the client to the server.
Responses—sent from the server to the client.

3.5.1 SIP Requests:  
SIP requests are distinguished by having a Request-Line for a start- line.  A Request-Line contains a method name, a Request-URI, and the protocol version separated by a single space (SP) character. [12]
    Table 3.1: Request Methods
Method
Description
INVITE
Initiates a call, changes call parameters
ACK
Confirms a final response for INVITE
BYE
Terminates a call.
CANCEL
Cancels searches and “ringing”.
OPTIONS
Queries the capabilities of the other side.
REGISTER
Registers with the Location Service.
INFO
Sends mid-session information that does not modify the session state.


3.5.2 SIP Responses: 
    Response messages contain numeric response codes. The SIP response code set is partly based on HTTP response codes. There are two types of responses and six classes.
    Response Types:
1. Provisional (1xx class): provisional responses are used by the server to indicate progress, but they do not terminate SIP transactions.
  	  2. Final (2xx, 3xx, 4xx, 5xx, 6xx classes): Final responses terminate SIP transaction

    Classes:
1xx = provisional, searching, ringing, queuing etc.
2xx = success
3xx = redirection, forwarding
4xx = request failure (client mistakes)
5xx = server failures
6xx = global failure (busy, refusal, not available anywhere)
The first digit of the Status-Code defines the class of response. The last two digits do not have any categorization role. [12]

Table 3.2:  Response Codes
100
Continue
408
Request Time out
180
Ringing
480
Unavailable
200
OK
481
Call-leg/Transaction does not exist
300
Multiple choices
482
Loop detected
301
Moved permanently
5xx
Server Error
302
Moved temporarily
600
Busy
400
Bad Request
603
Decline
401
Unauthorized
604
Doesn’t exist
403
Forbidden
606
Not acceptable

Message Parts: SIP messages are composed of the following three parts:
       Start Line: Every SIP message begins with a Start Line. The Start Line conveys the message type (method type in requests, and response code in responses) and the protocol version. The Start Line may be either a Request-line (requests) or a
          Status-line (responses), as follows:
                (i) The Request-line includes a Request URI, which indicates the user or service to which this request is being addressed. Unlike the “To” field, this address can be re-written by proxies.
               (ii) The Status-line holds the numeric Status-code and its associated textual phrase.

       Headers:   SIP header fields are used to convey message attributes and to modify message meaning. They are similar in syntax and semantics to HTTP header fields (in fact some headers are borrowed from HTTP) and thus always take the format: <name> :< value>
          However, SIP is not an extension of HTTP. Headers can span multiple lines. Some SIP headers such as Via, Contact, Route and Request-Route can appear multiple times in a message or, alternatively, can take multiple comma-separated values in a single header occurrence. The mandatory SIP headers are To, From, Max Forwards, Via, CSeq, Call-ID. The media capabilities of the devices at the user end can also be known.

     Body (Content):  A message Body is used to describe the session to be initiated (for example, in a multimedia session this may include audio and video codec types, sampling rates etc.), or alternatively it may be used to contain opaque textual or binary data of any type which relates in some way to the session. Message bodies can appear both in request and in response messages. SIP makes a clear distinction between signaling information, conveyed in the SIP Start Line and headers, and the session description information, which is outside the scope of SIP.
             Possible body types include:
SDP—Session Description Protocol (SDP).
Multipurpose Internet Mail Extensions (MIME).
Others—to be defined in the IETF and in specific implementations.

3.6 Intelligent Call Routing:
                   It is the smart way to route customer calls. A simple database stored on the server and accessible by an administrator workstation defines how calls should be routed. Updates to this table take effect immediately. Different tables may be set up for different departments, functions. [8]
Benefits of Intelligent Call Routing are:
 ■  Improves customer service by providing reliable routing of callers to the appropriate agent or expert.
 ■  Provides dynamic service levels based on customer tier.
■ Allows for simple redistribution of territories or assignments without changing auto attendant greetings or completing an expensive caller re-notification.
■ Route customers with credit problems directly to the credit department, saving support department time and better serving the customer.
■ Tracks how often and when each customer calls in order to determine appropriate charge back and staffing levels.

3.7 Presence Management:
                    In today’s increasingly complex world of communications, subscribers who wish to remain in touch at all times use an increasing range of devices and networks. Subscribers are faced with too many options often have difficulty communicating successfully.
The solution lies in presence management which allows the user to be available on many devices. The sip address which is unlike a telephone number allows the person to be contacted irrespective of the devices he is available on. The sip address irrespective of device remains the same. This allows more accurate communication without losing out on a call. [7]

3.8 Other Protocols used:
3.8.1 Session Description Protocol: 
        SDP is the protocol used to describe multimedia session announcement, multimedia session invitation and other forms of multimedia session initiation.
A multimedia session is defined, for these purposes, as a set of media streams that exist for duration of time. SDP is defined by RFC 2327. [9]

SDP PACKETS: SDP packets usually include the following information:
Session information
Session name and purpose.
Time(s) the session is active.
Since the resources necessary for participating in a session may be limited, it would be useful to include the following additional information:
Information about the bandwidth to be used by the session.
Contact information for the person responsible for the session.
Media information
Type of media, such as video and audio.
Transport protocol, such as RTP/UDP/IP and H.320
Media format, such as H.261 video and MPEG video.
SDP session descriptions may be concatenated together (the `v=' line indicating the start of a session description terminates the previous description).  Some lines in each description are required and some are optional but all must appear in exactly the order given here (the fixed order greatly enhances error detection and allows for a simple parser). Optional items are marked with a `*'.

Session description
        v=  (protocol version)
        o=  (owner/creator and session identifier).
        s=  (session name)
        i=* (session information)
        u=* (URI of description)
        e=* (email address)
        p=* (phone number)
        c=* (connection information - not required if included in all media)
        b=* (bandwidth information)
        One or more time descriptions (see below)
        z=* (time zone adjustments)
        k=* (encryption key)
        a=* (zero or more session attribute lines)
        Zero or more media descriptions (see below)

Media description
        m=  (media name and transport address)
        i=* (media title)
        c=* (connection information - optional if included at session-level)
        b=* (bandwidth information)
        k=* (encryption key)
        a=* (zero or more media attribute lines)

Time description
        t=  (time the session is active)
        r=* (zero or more repeat times)
Security Considerations
           SDP is a session description format that describes multimedia sessions.  A session description should not be trusted unless it has been obtained by an authenticated transport protocol from a trusted source.  Many different transport protocols may be used to distribute session description, and the nature of the authentication will differ from transport to transport. One transport that will frequently be used to distribute session descriptions is the Session Announcement Protocol (SAP).
3.8.2 Real-time Transport Protocol (or RTP): 
       RTP defines a standardized packet format for delivering audio and video over the Internet. It was developed by the Audio-Video Transport Working Group of the IETF and first published in 1996 as RFC 1889, and superseded by RFC 3550 in 2003. [9]
                                                        
                                                 Fig 3.2: RTP protocol stack
RTP is frequently used in streaming media systems as well as in videoconferencing and push to talk systems. For these it carries media streams controlled by H.323 or Session Initiation Protocol (SIP) signaling protocols, making it one of the technical foundations of the Voice over IP industry.
For using RTP, JMF API is needed. The Java Media Framework (JMF) is a Java library that enables audio, video and other time-based media to be added to Java applications and applets. This optional package, which can capture, play, stream, and transcode multiple media formats, extends the Java Platform, Standard Edition (Java SE) and allows development of cross-platform multimedia applications.
RTP is usually used in conjunction with the Real-time Transport Control Protocol (RTCP). While RTP carries the media streams (e.g., audio and video) or out-of-band signaling (DTMF), RTCP is used to monitor transmission statistics and quality of service QoS information. When used in conjunction, RTP is usually originated and received on even port numbers, whereas RTCP uses the next higher odd port 
