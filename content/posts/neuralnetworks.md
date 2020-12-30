---
title: "Neural Networks in Media"
date: 2017-01-01
draft: false
---

I wrote this at the end of my tenure at the NYT R&D Lab in 2016. I was trying to get at something about how the rich-get-richer cycle that AI encapsulates is important to pay attention to. Since I wrote it the effect has become blisteringly obvious, though whether or not it gets spoken about openly or if it's generally that interesting to people is not something I've kept up with. 

It's hard to write this sort of thing as a data scientist without sounding jealous or grumpy. I think I did OK though!

I'm recording it here for posterity.

---

# Abstract

Neural Networks - algorithms that learn complex relationships between media assets and their metadata - present interesting and powerful opportunities to media organisations, but at a cost that is not immediately apparent. By realisingunderstanding both the opportunities and the costs inherent to this technology, media organisations can make the careful decisions necessary to properly engage with neural network-based algorithms. 

From a media perspective, neural networks challenge the traditional notion of editorial effort in which conscious decisions are made (and argued) around the writing and publishing processes. Instead, when black box models are used to create and/or choose content to be published, editorial effort becomes a process of correctly training a decision-making machine to act in a way its trainers see fit.

The rapacious desire that neural networks have for training data has two immediate implications: 1) that structured data collection becomes the dominant problem, not that of building and training the neural networks themselves and 2) only those companies with the mindset and capacity to perform this collection at scale can successfully train and deploy worthwhile neural networks. 

That neural networks will only be effectively deployed by the large technology companies has, in turn, a set of impacts that form the basis for decisions a media organisation must address when thinking about this technology. Free, hosted services will enable rapid prototyping of the next wave of media technologies but, due to the very nature of learning machines, use of these services will aggressively improve the services themselves. It is important to realise that this feature of learning-based services is new and unique, and that their use could introduce an exponentially increasing dependency on the vendor.

# Introduction

Neural networks are a type of algorithm that can, after being shown a lot of labelled data, learn to predict labels for new examples they’ve not been exposed to before. They are remarkably malleable and through careful training can be encouraged to represent highly complex relationships between inputs and labels. Neural networks have been relatively common since the 90s but over the last few years, under the label “Deep Learning”, they have received a large amount of attention [?] from both academia and industry.  

Deep learning has arrived at the confluence of three advancements: an important improvement to the learning algorithms of complex neural networks, an availability of massively parallel computation in the form of Graphical Processing Units (GPUs), and the collection of huge structured data sets - the era of so called “Big Data”.

Together these advancements have allowed a number of organisations to push on advancing neural networks and notable gains have been made, especially in the machine vision and sequence prediction tasks. For the first time outside of a research setting, it is possible to give an algorithm a photo and get back a set of labels of a reliable quality [?], or the beginning of a sentence and get back a meaningful sentence ending [?]. 

These improvements are dramatic enough that they open up a new world of data-driven technologies in media. From archive processing, to live video captioning, these algorithms suggest interesting opportunities to those geared up to capitalise on them. For example: 
* Clarifai [?], an NYC based company looking to commercialise neural network backed services offers a photo management tool with automatically generated tags and relationships. 
* The artist Kyle McDonald, using an open-source neural network implementation [?], live captioned a point-of-view video [?] with captions that were remarkably accurate for a small saunter down the street.
* Generating summaries of text has received a new lease of attention from the deep learning communities [?, ?], including open source software to implement these algorithms. Readable auto-summarization suggests an opportunity for remixing existing articles, or facilitating the write-once publish-everywhere publishing model. 
* Similarly, both question-answering [?] and sentence modelling [?] networks have been developed in the literature. These promise new forms of interaction with text, suggesting custom responses to natural-language questions. 

This report explores some impacts of this technology on media organisations. We will avoid technical detail of neural networks, or the machine learning that surrounds them, though the references herein should provide ample jumping-off points. We will also avoid the various academic and social/technical histories of neural networks and machine learning (though see [?] for an introduction) as we want to focus exclusively on how this technology may affect media organisations. 

The remainder of this introduction gives a quick overview of the advances that have come together, fuelling the current attention in this style of algorithm. The rest of the report will focus on three areas: how building deep-learning based systems challenges notions of expertise and editorial; implications of the desire that deep learning has for large amounts of data; and how media organisations will actually use these technologies in practice. 

# Neural Networks, GPUs, and the era of Big Data

We can highlight three conditions that came together over the last 5 years that have enabled the new resurgence of neural networks. 

The first condition is a set of practical advances in the algorithms that train neural networks, and a realisation that the so-called “deep” networks are capable of building their own understanding of what’s important in a data set [?]. Learning can now take place inside networks with many layers, something which in turn enables the spectacular increases in accuracy for tasks such as image classification [?] and speech recognition [?].

The second condition is the availability of Graphical Processing Units (GPUs), both large and small. Neural networks are ideally suited to massively parallel computation due to their large but homogeneous architectures. The theoretical advances that allowed for the sudden increase in accuracy of neural networks was enabled by the massive parallelisation afforded by GPUs - dedicated pieces of hardware designed to do many simple operations all at once. On the large end is the NVIDIA Titan Z which boasts 5,760 processors, retailing for around 2200USD [?] at time of release. On the small end is the NVIDIA Jetson [?] - a complete computer with 192 GPU processors, capable of running complex neural networks and retailing for 200USD. GPU development has largely been driven by the huge market around computer gaming, but is now being aggressively capitalised on by parts of the machine learning community. 

This technology has allowed researchers to train neural networks, whose individual components are very simple and ideal for GPUs, with hundreds of thousands of neurons. Practically this means that the training procedures can result in a neural network that can capture very intricate relationships between an incredibly complex input (say, images) and a huge number of possible labels. 

The third condition is the explosion of available data starting some time after 2000. The internet, and the associated advancements in storage and transfer, has given rise to an epoch-defining increase in the creation and storage of data. While a lot of machine learning techniques are targeted at situations with a small amount of data, neural networks are targeted instead at a world that produces an abundance of data. In order to train an algorithm that can classify an image it hasn’t seen before, it has to train on many thousands of pre existing, labelled images. This was simply not possible during the first blush of neural network research in the 90s, but in the era of “Big Data” it becomes, for certain actors, entirely possible. 

These three conditions: the theoretical developments, commoditized massively parallel computation, and the availability of huge structured data sets have given rise to an increased attention to neural networks. They represent a particular kind of power, and a rather distinct philosophy of machine learning, that we believe will have a large impact on media in general. What follows is a set of speculations that are designed to illustrate some implications of neural networks and their adoption.  

# Teaching Machines

Three key points guide this first speculation:
* a neural network is a general purpose mechanism that maps input data to output data.
* a neural network starts off in an uninformed state - it knows nothing about the problem domain
* a neural network learns exclusively by being exposed to labelled data. 

These are such broad statements as to render them almost trivial, however they can’t be so generally applied to other techniques in the data sciences. They also capture an aspect of what’s important about neural networks: they don’t need, nor attempt to elucidate, a mechanistic understanding of the world; they just need example inputs and outputs. 

Neural networks can be thought of as quite distinct from the other dominant styles of machine learning. Machine learning is often concerned with building and training models: creating representations of processes that can be observed in the world. Models are, by and large, built to test some hypothesis or to make predictions.

Individual types of model often sit on a spectrum from white-box to black-box. White box models are those that describe the relationship between concrete things in the world. So Newton’s second law,  “force equals mass times acceleration”, would be considered a white-box model as every aspect of his equation relates to something Newton considered extant in the world. A “grey box” model doesn’t quite share the force of this 1-to-1 relationship, but does make assertions about relationships that, for the purposes of the modelling exercise, are important for a human to understand in some way. 

Neural networks live on the extreme black-box end of this spectrum. They are a declaration: that the important performance indicator is predictive ability, and that it should not matter to a human how the neural network represents the world it is being shown. To refer to neural networks as models at all becomes difficult, as the representation is of diminished importance in the face of such accurate prediction. We don’t learn from neural networks; they learn from us. 

In this context, then, neural networks are not programmed, they are taught [?]. They begin in an uninformed, naive state, and are then shown input/label pairs until they can successfully label data that they’ve not been shown before. This approach to learning denies the incorporation of specialist knowledge into the model’s architecture, something a lot of other types of model try to incorporate explicitly. Instead the specialist becomes that of a curator, assembling a corpus of input/output data.

The role of the data scientist in a media company is then to train the neural network as opposed to, say, building models of editorial effort, or audience behaviour. If it is required to predict an audience segment’s future behaviour, all that is required is data capturing relevant behaviour in the past. This is distinct from trying to build a model that represents e.g. that humans read the news more in the morning with their coffee, and immediately after lunch while they’re digesting. 

If a new photo is to be labelled, all that is required is appropriate photo/label pairs from the past. Again, this is distinct from trying to build a model that represents e.g. that photos have people in them and that people’s faces can be parameterised accurately from the distance between their eyes and nose and mouth. Neural networks do away with these attempts at modelling, producing much more accurate predictions in the process. 

Authorship of these algorithms therefore becomes that of showing the neural network the “correct” input/label pairs. So if a New York Times editor wants a neural network to caption a photo, the editor must show the neural network a lot of examples of how the NYT captions photos and not, say, how the Wall Street Journal captions photos.  A photo of two politicians talking in a board room could be tagged `[“barack obama”, “hillary clinton”, “handshake”]` or `[“politicians”, “suit”, “board room”, “table”]` or `[“black man”, “white woman”, “meeting”]`. All these tag sets are “accurate” in some sense, but have markedly different editorial intent. 

Similarly, within an organisation, there are multiple ways an image could be captioned that have different editorial intent. For example the same image within the New York Times may be labelled `[“Oscar Pistorius”, “Olympics”]` or `[“Oscar Pistorius”, “shooting”]` or `[“Oscar Pistorius”, “blades”]` that depends a great deal on the editorial intent for a particular article. The only way a neural network can distinguish the intent here is to be shown appropriate examples beforehand. 

To train a neural network the media organisation needs to collect many hundreds of thousands of these photo/tagset pairs: aside from the obvious practical problem of collecting this much data in the first place, the media organisation faces an even harder problem in maintaining an editorial voice within this data set. There are two main reasons for this. 

The first is that, because of the neural network’s appetite for data, it is tempting to gather any and all data that can be found and feed it to the training algorithm. Avoiding data points that do not agree with the attempted editorial intent makes gathering a data set of the appropriate size even more expensive. 

The second reason is that it is very hard to assess the editorial intent of an extremely large data set [?]. For example, in the case of image recognition for a media organisation, the input/label pair could be a news photo and a set of nouns contained in the photo. From the point of view of successful prediction, the nouns can essentially be anything, as long as the labelling is applied in a mostly consistent manner. Therefore, unless the media organisation is in explicit control of the creation of a data set, it is unclear how to verify accuracy, tone, bias, point of view etc. of many hundreds of thousands labeled examples. 

# Human Intelligence Tasks

Training a neural network, especially for image classification, requires a lot of labelled data. Labels are the difficult part of this equation: it’s relatively easy for a media organisation to collect an archive’s worth of image data, but assembling labelled data for each photo in the archive is labour intensive. 

There are a few major approaches that people have taken to assembling these labels using human labour, which we will refer to in general as “Human Intelligence Tasks” (see [?]): 
* marketplace crowdsourcing: Amazon’s Mechanical Turk [?] and Crowdflower [?] are the main, general purpose, crowdsourcing marketplaces. Here tasks are distributed through a website or apps [?] and are completed for a fee. 
* volunteer crowdsourcing: many organisations ask readers to help label collected assets as a volunteer effort. The New York Public Library has released a series of such projects, for example Emigrant City [?] encourages readers to help transcribe real estate records. The New York Times R&D lab released Madison [?] to help transcribe archived print adverts. The benefit to the crowd here is access to the archival material. 
* indirect crowdsourcing: a common task on the internet is to prove that you’re a human, protecting websites from aggressive automated access. One of the most popular mechanisms for this is to cause the human to solve a human intelligence task which, by definition, is impossible for a computer. The most popular service for deploying these tasks is google’s reCAPTCHA [?] which prompts the human to label a google-owned asset. Google claims hundreds of millions of CAPTCHAs are solved each day. 

Arguably the indirect approach is the most successful in terms of labels/expense, though notably only for the owner of the service. The marketplace and volunteer approaches require the human to be actively engaged with the task, rather than treating it as a momentary chore to access some desired resource. This active engagement allows for more complex tasks to be completed, but limits the achievable label/expense ratio. 

The other class of labelling mechanism, that wouldn’t typically be referred to as “crowdsourcing”, is label inference. This is where use of a service, say an image search engine or social media platform, generates labels through the natural course of its use. As a simple example, when a search query is made and an image is returned that satisfies the query in some manner, it is possible to now label that image with the search query. After many such query/response patterns, a consistent label can be inferred for the satisfying image by using the collected queries it satisfies. This idea can be extended to multiple services and used to build complex labels [?]. 

In this way, many structured data sets can be coerced into a neural network’s training set, as long as the set captures the desired relationship that is to be learned. The mindset that has given rise to much of the “Big Data” era and that we speculate will continue to drive service design (outside the EU), is that structured data will be valuable for training algorithms that don’t exist yet. 

This mindset is already, and obviously, starting to benefit the technology companies that have been organised in this way for many years. For example, it has been suggested [?] that one way Google might use imagery and LIDAR data collected using their street-view cars is for training a future self-driving car algorithm. Similarly it’s not hard to imagine Google’s image search service proving helpful when assembling something like their Machine Vision API [?]. Facebook has been collecting and tagging its user’s photos for over ten years at the time of writing, and has been performing automatic facial recognition for over five years [?] - an incredible training set for possible future algorithms. 

# Neural Networks As A Service

At this point, training a neural network has become well within the capacity of a data science organisation within a media company. Access to both neural-network software libraries [?, ?, ?, ?] and commoditised GPUs is straightforward and cheap. All this means that training neural networks is not the critical problem when deploying these techniques. Instead it is the collection of labelled data that is the limiting step. 

“Data” here is two things: inputs and labels. Inputs, from a media perspective, are essentially images or blocks of text; outputs are descriptive labels. Collecting the images and text is something a media company already knows how to do well; labelling that data at a scale that makes it useful is a much harder task, as discussed in the previous section. 

Only a handful of companies have the capacity, and the mindset, to think in terms of collecting data for training future algorithms as part of their every-day business, and this has allowed them to provide neural network based services for others to use. This happens both as an extension of that mindset - creating an API is an excellent way of evaluating the success of your algorithms and, potentially, collect more data to help with future training - and because these services will cement their position as marketplace leaders. Facebook, Google, and Amazon have at least a decade’s head start in collecting input/output data, machine learning expertise, and a data-focused product design mindset, putting them at tremendous advantage over even the most powerful of traditional media companies.

As an example, the Google Machine Vision API [?] allows its users to label images, perform Optical Character Recognition (OCR), infer places from images, perform facial/emotional recognition, and detect “inappropriate” (as defined by Google) images. This is at a (maximum) price of $5USD per 1000 images, with significant bulk discounts, and a generous free tier for small numbers of requests. Google are able to leverage both their in-house expertise and their extensive data sets to make a cheap, high quality service that would be incredibly expensive, and practically infeasible, to reproduce elsewhere. 

So to build on top of the opportunities that deep learning has to offer, the news organisation faces a choice. Either hire expensive machine learning specialists, purchase and deploy some new hardware, label a very large amount of data, and train a set of neural networks; or call a very cheap API. The choice is obviously clear in the situation that the API provides the type of labelling required. Ceding the ground this technology represents will benefit the media company in the short term, providing some of the impressive technical capacities of neural networks with extremely low effort. 

This implies, then, that a marketplace will form to provide neural-network based services. How the players in this market will differentiate themselves is an interesting thought experiment. For example:
* price: The current APIs, Google Machine Vision and Clarifai being two image-focused examples, are already cheap. As providers realise the training benefit inherent in customers using their APIs we can imagine a decrease in the cost of these APIs until they become free. Price, therefore, is only a short term differentiator. 
* licensing: The Google API currently does not use supplied images for training; Clarifai does. Licensing options that prohibit the service provider from retaining the supplied images, or from using the training to enhance services for other customers, would be important to many media companies.
* voice: Being able to define the “voice” or “style” of a neural network would drive adoption. If the New York Times could rely on a “progressive” convolutional neural network, this would be worth more than a general-purpose or uncharacterised voice. 
* speed: The Google API is currently not fast enough to process individual frames of a video to enable live transcription. The Clarifai API is fast enough. Speed is a good example of a technical differentiator that is more to do with the service deployment, rather than the neural network itself. 

It is important to emphasise that the cost-of-entry into the world of neural-networks is incredibly high, and it is not the cost of training or deploying the neural network. It is the cost of collecting labelled data and the cost of switching to a mindset that treats every corporate action as an opportunity for collecting input/output data. For traditional media companies the game is, most likely, already over. What remains is how to operate as a customer in a marketplace with an extremely small number of vendors.

# Conclusion

Media companies can gain so much from this technology, especially as `post-app` or `thin media` speculations start to come true  [?, ? , ?, ?, ?], which will require both complex image and text processing to be successful, and promote a more data-focused approach to interface design. 

## Example: The Neural CMS

A Content Management System (CMS) provides an interesting framework to outline the opportunities for neural network backed services. Here are some example of how these services could have an impact on the CMS:
* Text markup: a neural network backed text editor could encourage detailed markup [?] by using a recurrent neural network to predict possible tags for blocks of text.
* Summarisation: a well trained neural network could produce automatic summaries on the fly, both of an individual document, or of groups of documents for a long running story or package. This would allow someone writing or producing a piece to understand, as it was being written, how the piece would appear on extremely small screens (like a watch) and, potentially, extremely large screens, like a billboard. 
* Photo and video indexing: a convolutional neural network could extract tags from photos and videos, allowing them to be indexed, and searched, independently of the articles they ran with. This would allow photos and videos to be treated as fully-fledged documents in their own right in an otherwise text-centric CMS. 
* Video captioning: videos can be automatically captioned, using full sentences, allowing a video to be stored, tagged, and consumed as text. 
* Test variant generation: predictably high performing variants of SEO terms can be generated automatically, allowing A/B or Bandit testing to be performed automatically.
* Promotional predictions: a neural network that can learn the response of an audience under particular conditions (time of day, weather, competing stories, current segment breakdowns) to a set of complex promotional events (sequences of tweets, homepage promotions, facebook posts, email alerts, push notifications etc) would allow for both traffic prediction of human-suggested promotional activities and an automatically choreographed set of promotions designed to maximise traffic over multiple stories. 

## Pragmatics

The reality of the situation is that most media companies do not have the resources, or the mindset, necessary to collect the amount of labelled data necessary to train their own algorithms, and so will rely on APIs provided by a few large tech companies, who are already a long way ahead.  This will further embed the power held by these companies, amplified by the fact that third parties using these services will, as a side effect, improve the neural networks that back them. 

Under these conditions there are two key decisions a media company has to make. One is whether or not to engage at all, and the second is whether or not to try and keep the technology in house. 

On the first point, we feel that there is a clear danger in employing this style of algorithm in a media organisation, but that the opportunities far outweigh the risks. The danger is that the media organisation becomes dependent on an algorithm that is, by design, unknowable and that has been trained using data that the media organisation has not controlled. Researchers understand how the training algorithms work, and how individual components of the neural network operate. But to even question the legibility of a neural network, an important question for other styles of algorithm [?], would be to misunderstand how general-purpose, and how complex a neural network is. For companies that think about technology as a mechanism for amplifying their editorial voice, inserting an entirely black-box algorithm into the pipeline should be cause for concern. Having said this, careful deployment of neural networks represent an exciting opportunity to explore the future of online publishing, and they should not be ignored. 

On the second point we feel that the tech companies are so far ahead that it would be prohibitively difficult to try and keep technology in house. While this represents an extremely uncomfortable ceding of power to tech companies who are also building a new wave of publishing platforms, this would allow the media organisation to focus on the application, rather than the development, of neural networks. 

The main problem with this approach is that the media organisation will have no control of editorial voice of third party systems, meaning that any deployment will, in the short to medium term, have to form part of a human powered process, rather than being entirely autonomous. 

Finally, we would like to reinforce a message that has been running throughout this report. The nature of learning machines, such as neural networks, implies that they can improve simply through regular use of the services that they power. So an image captioning service can be built that not only provides the service to the client organisation but that can use the data being passed through it to improve. This kind of learning is not typically considered a transfer of intellectual property from the client to the vendor, rather it is by default considered a new creative work that is owned completely by the vendor. 

This implies that the most popular service will in fact become the best service as the data-collection problem is solved implicitly through use of the service itself. When a media organisation chooses to engage with this sort of service, it must consider that it is generating potentially valuable intellectual property that it has no access or rights to. In the competitive landscape that a media company inhabits, especially one that owns its own platform, giving away IP to potential platform competitors must be carefully evaluated. 


