#  

#  

# The Geometry of Information Retrieval  

Information retrieval, IR, is the science of extracting information from documents. It can be viewed in a number of ways: logical, probabilistic and vector space models are some of the most important. In this book, the author, one of the leading researchers in the area, shows how these three views can be combined in one mathematical framework, the very one used to formulate the general principles of quantum mechanics. Using this framework, van Rijsbergen presents a new theory for the foundations of IR, in particular a new theory of measurement. He shows how a document can be represented as a vector in Hilbert space, and the document’s relevance by an Hermitian operator. All the usual quantum-mechanical notions, such as uncertainty, superposition and observable, have their IR-theoretic analogues. But the approach is more than just analogy: the standard theorems can be applied to address problems in IR, such as pseudo-relevance feedback, relevance feedback and ostensive retrieval. The relation with quantum computing is also examined. To help keep the book self-contained, appendices with background material on physics and mathematics are included, and each chapter ends with some suggestions for further reading. This is an important book for all those working in IR, AI and natural language processing.  

Keith van Rijsbergen’s  research has, since 1969, been devoted to information retrieval, working on both theoretical and experimental aspects. His current research is concerned with the design of appropriate logics to model the ﬂow of information and the application of Hilbert space theory to content-based IR. This is his third book on IR: his ﬁrst is now regarded as the classic text in the area. In addition he has published over 100 research papers and is a regular speaker at major IR conferences. Keith is a Fellow of the IEE, BCS, ACM, and the Royal Society of Edinburgh. In 1993 he was appointed Editor-in-Chief of  The Computer Journal,  an appointment he held until 2000. He is an associate editor of  Information Processing and Management , on the editorial board of  Information Retrieval , and on the advisory board of the  Journal of Web Semantics.  He has served as a programme committee member and editorial board member of the major IR conferences and journals. He is a non-executive director of a start-up: Virtual Mirrors Ltd.  

# The Geometry of Information Retrieval C. J. VAN RIJSBERGEN  

cambridge university press Cambridge, New York, Melbourne, Madrid, Cape Town, Singapore, São Paulo  

Cambridge University Press The Edinburgh Building, Cambridge  cb2 2ru , UK Published in the United States of America by Cambridge University Press, New York  

www.cambridge.org Information on this title: www.cambridge.org/9780521838054  

$\copyright$   C. J. van Rijsbergen 2004  

This publication is in copyright. Subject to statutory exception and to the provision of relevant collective licensing agreements, no reproduction of any part may take place without the written permission of Cambridge University Press.  

First published in print format  2004  

isbn-13    978-0-511-21675-6 eBook (NetLibrary) isbn-10    0-511-21675-0 eBook (NetLibrary) isbn-13    978-0-521-83805-4 hardback isbn-10    0-521-83805-3 hardback  

Cambridge University Press has no responsibility for the persistence or accuracy of  url s for external or third-party internet websites referred to in this publication, and does not guarantee that any content on such websites is, or will remain, accurate or appropriate.  

To make a start, Out of particulars And make them general, rolling Up the sum, by defective means  

Paterson : Book I William Carlos Williams, 1992  

for Nicola  

# Contents  

Preface page  ix Prologue 1 1 Introduction 15 2 On sets and kinds for IR 28 3 Vector and Hilbert spaces 41 4 Linear transformations, operators and matrices 50 5 Conditional logic in IR 62 6 The geometry of IR 73 Appendix I Linear algebra 101 Appendix II Quantum mechanics 109 Appendix III Probability 116 Bibliography 120 Author index 145 Index 148  

This book begins and ends in information retrieval, but travels through a route constructed in an abstract way. In particular it goes through some of the most interestingandimportantmodelsforinformationretrieval,avectorspacemodel, a probabilistic model and a logical model, and shows how these three and possibly others can be described and represented in Hilbert space. The reasoning that occurs within each one of these models is formulated algebraically and can be shown to depend essentially on the geometry of the information space. The geometry can be seen as a ‘language’ for expressing the different models of information retrieval.  

The approach taken is to structure these developments ﬁrmly in terms of the mathematics of Hilbert spaces and linear operators. This is of course the approach used in quantum mechanics. It is remarkable that the application of Hilbert space mathematics to information retrieval is very similar to its appli- cation to quantum mechanics. A document in IR can be represented as a vector in Hilbert space, and an observable such as ‘relevance’ or ‘aboutness’ can be represented by a Hermitian operator. However, this is emphatically not a book about quantum mechanics but about using the same language, the mathematical language of quantum mechanics, for the description of information retrieval. It turns out to be very convenient that quantum mechanics provides a ready-made interpretation of this language. It is as if in physics we have an example seman- tics for the language, and as such it will be used extensively to motivate a similar but different interpretation for IR. We introduce an appropriate logic and prob- ability theory for information spaces guided by their introduction into quantum mechanics. Gleason’s Theorem, which speciﬁes an algorithm for computing probabilities associated with subspaces in Hilbert space, is of critical impor- tance in quantum mechanics and will turn out to be central for the same reasons in information retrieval. Whereas quantum theory is about a theory of mea- surement for  natural  systems, The Geometry of Information Retrieval is about such a theory for  artiﬁcial  systems, and in particular for information retrieval. The important notions in quantum mechanics, state vector, observable, uncer- tainty, complementarity, superposition and compatibility readily translate into analogous notions in information retrieval, and hence the theorems of quantum theory become available as theorems in IR.  

One of the main aims of this book is to present the requisite mathematics to explore in detail the foundation of information retrieval as a parallel to that of quantum mechanics. The material is principally addressed to students and researchers in information retrieval but will also be of interest to those working in such disciplines as AI and quantum computation. An attempt is made to lay a sound mathematical foundation for reasoning about existing models in IR sufﬁcient for their modiﬁcation and extension. The hope is that the treatment will inspire and enable the invention of new models. All the mathematics is introduced in an elementary fashion, step-by-step, making copious references to matching developments in quantum mechanics. Any reader with a good grasp of high school mathematics, or A-level equivalent, should be able to follow the mathematics from ﬁrst principles. One exception to this is the material in the Prologue, where some more advanced notions are rapidly introduced, as is often the case in dialogue, but even there a quick consultation of the appropriate appendices would clarify the mathematics.  

Although the material is not about quantum computation, it could easily be adopted as an elementary introduction to that subject. The mathematics required to understand most discussions on quantum computation is covered. It will be interesting to see if the approach taken to modelling IR can be mapped onto a quantum computer architecture. In the quantum computation literature the Dirac notation is used as a  lingua franca , and it is also used here and is explained in some detail as it is needed.  

Students and researchers in IR are happy to use mathematics to deﬁne and specify algorithms to implement sophisticated search strategies, but they seem to be notoriously resistant to investing energy and effort into acquiring new mathematics. Thus there is a threshold to be overcome in convincing a person to take the time to understand the mathematics that is here. For this reason we begin with a Prologue. In it fundamental concepts are presented and discussed with only a little use of mathematics, to introduce by way of a dialogue the new way of thinking about IR. It is hoped that illustrating the material in this way will overcome some of the reader’s resistance to venturing into this new mathematical territory for IR.  

A further ﬁve chapters followed by three technical appendices and an exten- sive annotated Bibliography constitute the full extent of the book. The chapters make up a progression. Chapter 1, the Introduction, goes some way to showing the extent to which the material depends on ideas from quantum mechanics whilst at the same time motivating the shift in thinking about IR notions. Chapter 2 gives an account of traditional Boolean algebra based on set theory and shows how non-Boolean structures arise naturally when classes are no longer sets, but are redeﬁned in an appropriate way. An illustration of the breakdown of the law of distribution in logic then gives rise to non-classical logic. Chapter 3 introduces vector and Hilbert spaces from ﬁrst principles, leading to Chapter 4 which describes linear operators, their representation and properties as vehicles for measurement and observation. Chapter 5 is the ﬁrst serious IR application for the foregoing theory. It builds on the earlier work of many researchers on logics for IR and it shows how conditionals in logic can be represented as objects in Hilbert space. Chapter 6, by far the longest, takes the elementary theory presented thus far and recasts it, using the Dirac notation, so that it can be applied to a number of speciﬁc problems in IR, for example, pseudo-relevance feedback, relevance feedback and ostensive retrieval.  

Each chapter concludes with some suggestions for further reading, thus providing guidance for possible extensions. In general the references collected at the end of the book are extensively annotated. One reason for this is that readers, not necessarily acquainted with quantum mechanics or its mathematics, may enjoy further clariﬁcation as to why pursuing any further reference may be worthwhile. Scanning the bibliography with its annotations is intended to provide useful information about the context for the ideas in the book. A given reference may refer to a number of others because they relate to the same topic, or provide a commentary on the given one.  

There are three detailed appendices. The ﬁrst one gives a potted introduction to linear algebra for those who wish to refresh their memories on that subject. It also conveniently contains a summary of the Dirac notation which takes some getting used to. The second appendix is a self-contained introduction to quantum mechanics, and it uses the Dirac notation explained in the previous appendix.It also contains a simple proof of the Heisenberg Uncertainty Principle which does not depend on any physics. The ﬁnal appendix gives the classical axioms for probability theory and shows how they are extended to quantum probability.  

There a number of ways of reading this book. The obvious way is to read it from beginning to end, and in fact it has been designed for that. Another way is to read the Prologue, the Introduction and the appendices, skipping the intervening chapters on a ﬁrst pass; this would give the reader a conceptual grasp of the material without a detailed understanding of the mathematics. A third way is to read the Prologue last, and then the bulk of the book will provide grounding for some of the advanced mathematical ideas that are introduced rapidly in the Prologue. One can also skip all the descriptive and motivational material and start immediately with the mathematics, for that one begins at Chapter 2, and continues to the end. A ﬁfth way is to read only Chapter 6, the geometry of IR, and consult the relevant earlier chapters as needed.  

There are many people who have made the writing of this book possible. Above all I would like to thank Juliet and Nicola van Rijsbergen for detailed and constructive comments on earlier drafts of the manuscripts, and for the good humour with which they coped with my frustrations. Mounia Lalmas, Thomas Roelleke and Peter Bruza I thank for technical comments on an early draft. Elliott Sober I thank for help with establishing the origin of some of the quotations as well as helping me clarify some thinking. Dealing with a publisher can sometimes be fraught with difﬁculties; fortunately David Tranah of CUP ensured that it was in fact wonderfully straightforward and agreeable, for which I express my appreciation; I also thank him for his constant encouragement. The ideas for the monograph were conceived during 2000–1 whilst I was on sab- batical at Cambridge University visiting the Computer Laboratory, Department of Engineering and King’s College, all of which institutions deserve thanks for hosting me and making it possible to think and write. Taking on a task such as this inevitably means that less time is available for other things, and here I would like to express my appreciation to the IR group at Glasgow University for their patience. Finally, I would like record my intellectual debt to Bill Maron whose ideas in many ways foreshadowed some of mine, also to the writings of John von Neumann for his insights on geometry, logic and probability without which I could not have begun.  

Where did that come from? Strictly Ballroom , ﬁlm, directed by Baz Luhrmann, Australia: M&A Film Corporation, 1992.  

# Scene  

A sunny ofﬁce overlooking a cityscape of Victorian roofs and elm trees. K, an academic of some seniority judging by his white beard, and the capaciousness of his bookshelves, is sitting at his desk. The sign outside his door reads ‘Please disturb’ .  

B: (A younger academic) enters without knocking, shortly followed by N (not so young). B: I hear that you have been re-inventing IR. K: Well, I am writing a book. B: Yes, the story is that you have been looking at quantum mechanics, in order to specify a new model. Also (looks at N) that you are looking at quantum computation. K: I have certainly been looking at quantum mechanics, but  not  because I want to specify a new model; I am looking at quantum mechanics because it gives insight into how one might combine probability, logic and vector spaces into one formalism. The role of quantum computation in all this is not clear yet. It may be that having reformulated IR in this way, using the language of quantum mechanics, that it will be obvious how quantum computation may help at the algorithmic level, but I have not been thinking that far . . . N: (Interrupting) Well, I listen patiently as ever – but it seems to me that you are – yet again – taking an entirely system-based approach to IR  

leaving no room for the user. For years now I have been saying that we need to spend more time on improving the interaction of the user with any  system. Support for the user will make a bigger difference than any  

marginal improvements to a system. A new . . . K: (Interrupting in turn) I know you think we should stop developing new theories and models and instead spend the time making existing ones work from a user perspective. Well, in a way that is what all this is about. Currently, we really do not have a way of describing formally, or in theoretical terms, how a user interacts with an IR system. I think . . . N: – here we go. It has to be ‘formal’ – K: we need a new paradigm, and the QM paradigm – N: (Interrupting for the third time) Why? Why do we need this extra formalism? We have spent years describing how a user interacts with an IR system. K: (Holds up hand) Hang on. We have had this argument over and over again. My reply has always been that if you do not formally describe or specify something then trying to arrive at a computational form becomes nigh impossible. Or if you do achieve a computational form without formal description then transferring a design from one approach or system to another becomes a nightmare. There is also the scientiﬁc imperative, that we cannot hope to make predictions about systems if we cannot reason about their underlying structure, and for this we need some kind of formality, and, dare I say it, – N: I suppose I can’t stop you – K: a theory. Einstein always claimed that you need a theory to tell you what to measure. N: Must you drag Einstein into this? B: Let me get a word in edgewise. One could argue that a computer pro- gramme is a description, or a formal theory of a system. Why do we need more than that? K: (Becomes instantly enthusiastic) Good question. It is certainly true that a computer program can be considered as a formal description of a process or a theory. Unfortunately it is very difﬁcult to reason about such a description, and it is difﬁcult to recover the semantics. What’s more, computer programs are strongly inﬂuenced by the design of the digital computer which they run, that is, their von Neumann architecture. In developing this new IR paradigm I intend it perhaps to be implemented on a quantum computer. N: Delusions of grandeur. So, tell us what is the essence or central idea of your new way of looking at things?  

K: (Becomes even more enthusiastic) This will take some time, how long have you got? B, N: We have got all afternoon. K: (Hesitates) Of course, it would easier for you to understand what I am doing if you knew some elementary quantum mechanics. Let’s see: you could start with Hughes’ book on ‘The Structure and Interpretation of Quantum Mechanics’ . . . N: I said we had this afternoon, not the next ﬁve years. K: . . . I found his account invaluable to understanding some of the basics. B: Can’t you just give us the gist? K: (Gets up and inspects his bookshelf) Well, the story really begins with von Neumann. As you know, in the thirties he wrote a now famous book on the foundations of quantum mechanics. One could argue that all later developments in quantum logic and probability are footnotes to his book. Of course von Neumann did not  do  QM, like say Feynman and Dirac, he theorised about it. He took the pioneering work of Bohr, Schr¨ odinger, Heisenberg, Born and others, and tried to construct a con- sistent formal theory for QM It is much in the same spirit as what I am attempting for IR. N: (Laughs) When I ascribed you delusions of grandeur I underestimated you. Are you now equating QM and IR in importance? Or merely yourself with von Neumann? In IR we deal only with artefacts and the way humans interact with them. Everything is man made. Whereas in QM we attempt to describe a piece of reality and many of the paradoxes arise because we are uncertain how to go about that. K: (Focusing on the last point) Ah, exactly. You have put your ﬁnger on the problem. Both in IR and QM we are uncertain about how to describe things – be they real or artiﬁcial. In QM we have the problem of measurement; we don’t know how to model the result of an observa- tion which arises from the interaction of an ‘observable’ with a piece of reality. In IR we face the same problem when we attempt to model the interaction of a ‘user’ with an artefact. B: (Gloomily) This is all getting a bit abstract for me. How about you try to make it more concrete? K: (Cheerfully now) Well imagine the world in IR  before  keywords or index terms. A document, then, was not simply a set of words, it was much more: it was a set of ideas, a set of concepts, a story, etc., in other words a very abstract object. It is an accident of history that a representation of a document is so directly related to the text in it. If IR had started with documents that were images then such a dictionary  

kind of representation would not have arisen immediately. So let us begin by leaving the representation of a document unspeciﬁed. That does not mean that there will be none, it simply means it will not be  

deﬁned in advance. B: (Even gloomier) Great. So how do I get a computer to manipulate it – this piece of ﬁction? K: Actually that is exactly what it is – a document is a kind of ﬁctive object. Strangely enough Schr¨ odinger . . . N: (As an aside) Here we go with the name dropping again. K: (continues, ignoring N) . . . in his conception of the state-vector for QM envisaged it in the same way. He thought of the state-vector as an object encapsulating all the possible results of potential measurements. Let me quote: ‘It (  $\psi$  -function) is now the means for predicting probability of measurement results. In it is embodied the momentarily attained sum of theoretically based future expectation, somewhat as laid down in a catalogue.’ 1   Thus a state-vector representing a document may be viewed the same way – it is an object that encapsulates the answers to all possible queries. N: (Perks up) Ah, I can relate to this. You mean a document is deﬁned with respect to the queries that a user might ask of it? K: Yes, in more than one way, as will emerge later. By the way, one could view Maron and Kuhns’ original paper on probabilistic indexing in this sort of way. Indeed, Donald Mackay (1969, 1950), who worked with Maron, anticipated the use of QM in theorising about IR. N: Good, keep going; we seem to be getting somewhere at last. K: So what have we got? We have a collection of artefacts each of which is represented by a highly abstract object called a ‘state-vector’. Of course using the term ‘vector’ gives the game away a little. These abstract objects are going to live in some kind of space (an information space), and it will come as no surprise to you that it will be a vector space, an inﬁnite-dimensional vector space: a Hilbert space. B: (With some frustration) Terriﬁc. After all this verbiage we end up with a vector space, which is a traditional IR model. So, apart from being able to add ourselves as footnotes to von Neumann, what is the big deal? K: The big deal is that we do not say in advance what the vectors in this space look like. All we require is a notion of dimensionality, which can be inﬁnite, and objects that satisfy the axioms of a vector space, for example, vectors can be added and multiplied by scalars. Moreover, the  

space has a geometry given by an inner product which allows one to deﬁne a distance on the space. The fact that it is inﬁnite is not immedi-  

ately important, but there is no reason to restrict the dimensionality. B: Why do you talk of scalars and not of real numbers? K: You noticed that did you? Well, scalars here can be complex numbers. N: Hold it, are you saying that we can attach a meaning to complex or for that matter imaginary numbers in IR? K: No, I am not saying that. I am implying that we do not need to restrict our representational power to just real numbers. Rest assured that our observation or measurements will always deliver a real number, but it may be that we represent things on the way by complex numbers. There are many examples in mathematics where this is done, in addition to quantum mechanics, for example, Fourier analysis. B: I don’t buy this. Why introduce what appears to be an unnecessary complexity into the representation? What on earth would you want to represent with complex numbers? K: To be honest I am not sure of this yet. But a simple example would arise in standard text retrieval where both term-frequency and document- frequency counts are used (per term, or per dimension) during a match- ing process. I imagine that we may wish to represent that combination of features in such a way that algebraic operations on them become easier. Right now when we combine  tf  and  idf  their identities are lost at the moment of combination. N: So, from a mathematical, or algorithmic, point of view this may make sense. But, tell me, are you expecting the user to formulate their queries using complex numbers? If so, you can forget it. K: No, of course not. But just as a person may write down a polynomial with real coefﬁcients which has  complex roots , a user may write down a query which from another point of view may end up being represented by complex numbers. The user is only expected to generate the point of view, and in changing it the query will change. N: (With some impatience) This sounds great but I do not fully understand it. What do you mean by a ‘point of view’? B: Yes, what do you mean? I am lost now. K: In conventional index term based retrieval the point of view in the vector space model is given by the axes in the space corresponding to the index terms in the query. Thus, if the query is   $(a,b,c,.\ .\ .)$   then    $a$   might lie along the  $x\cdot$  -axis,  $b$   the  $y$  -axis,  $c$   the  $z$  -axis, etc. Usually these are assumed to be orthogonal and linearly independent. Notice how convenient it is that the user has speciﬁed a set of axes. Now imagine that the query is  

simply an abstract vector in the space, we would still have to deﬁne it with respect to the basis of the space, but it would be up to us, or the user, to refer the objects in the space to different bases depending on their point of view. A change of basis constitutes a change of point of  

B: Well, I am not sure this buys us anything but I’ll hang in there for the moment. I see that you are still talking about queries as vectors. I infer that much of what you have said so far is a dressed up version of the standard vector space model of IR. Am I right? K: You are right. I am trying to inspire the introduction of some of the new ways of talking by referring to the old way. N: Get on with it – I am still waiting too. K: All right. But ﬁrst here is a small example of how we can go beyond standard vector space ideology. By assuming that the query is a vector in a high (maybe inﬁnite) dimensional space, we are making assumptions about the dimensions that are not mentioned in the query. We could assume that those components are zero, or have some other default value. Why? No good reason, and perhaps the query would be better represented by a  subspace , the subspace spanned by the basis vectors that are mentioned in the query. So we have grasped the need for talking about subspaces. The problem is how to handle that symbolically. More about this later. (B and N look bored, so K quickly moves on) K: Given the space of objects is a Hilbert space which we may fondly call an information space. How do we interact with it? N: (With a sigh of relief) At last something about interaction. B: Shut up, N. Let him talk. Although, I am still puzzled about how you will interact with these objects when you do not describe them explicitly in any way. K: (With a grin) That is right. I forgot to tell you that. Once you have speci- ﬁed the basis (point of view) for the space, you can express the object in terms of the basis. This is done by projecting the object onto the different basis vectors. The effect of this is to give a ‘co-ordinate’ for the object with respect to each basis vector. It is a bit like deﬁning an object by giving the answers to a set of simple questions, one question for each basis vector. If the object (state-vector) is normalised these projections are given by calculating the inner product between each basis vector and the state-vector. Of course, if we allow complex numbers then we would need to take the modulus (size) of the inner product to get a real number. In the case where we have a real Hilbert space, the state-vector  

is simply expanded as a real linear combination of the basis vectors. The expansion would differ from basis to basis.  

You are getting too technical again; let’s get back to the issue of inter- action.  

B: Yes, let’s.  

K: The basic idea is that an observable, such as a query or a single term, is to be represented by a linear operator which is self-adjoint in the Hilbert space. This means that in the ﬁnite case it corresponds to a matrix which can have complex numbers as entries but is such that the conjugate transpose is equal to itself. Let me illustrate. If A represents an observable, then A is self-adjoint if   $\mathrm{A}=\mathrm{A}^{*}$  .  

(K writes some symbols on the white board)  

$$
\mathbf{A}={\binom{a\quad b}{c\quad d}}
$$  

$$
\mathbf{A}^{*}={\overline{{\mathbf{A}^{\prime}}}}=\left({\frac{\overline{{a}}}{b}}\quad{\frac{\overline{{c}}}{d}}\right)=\mathbf{A}
$$  

$$
\mathrm{also}\ b=\overline{{c}},\,\overline{{b}}=c.
$$  

An example is  

$$
\mathbf{A}={\binom{1}{\mathbf{i}}}-{\binom{\mathrm{i}}{2}}
$$  

$$
\mathbf{A}^{*}={\overline{{\left(\begin{array}{l l}{1}&{-\mathrm{i}}\\ {\mathrm{i}}&{2}\end{array}\right)}}}^{\prime}=\left(\begin{array}{l l}{1}&{-\mathrm{i}}\\ {\mathrm{i}}&{2}\end{array}\right)=\mathbf{A}.
$$  

K: I know what you are going to say, what has this got to do with queries and users?  

N, B: How did you guess, so what has it got to do with them?  

K: Bear with me a little longer. The notion of representation is a little indirect here. In quantum mechanics the idea is that the value of an observable is given by the eigenvalues of the matrix.   The beauty is that the eigenvalues of a self-adjoint matrix are always  real , even though the entries in the matrix may be complex. So here we come back to the fact that our representation may involve complex numbers but when we make a measurement, that is interact, we only get real results.  

B: Hang on a bit, you said that the value of an observable is an eigenvalue, any eigenvalue? So, how do I know which one? Let me take a simple  

know which? Is this the right question to ask? K: We are now getting to the meat of it. If your observable represents a two- valued question, ‘1’ means ‘yes’ and   $^{\bullet}0^{\bullet}$   means ‘no’, then determining which answer is a matter of  probability . For example, if your observable was to determine whether an object was about the concept ‘house’, then there would be two eigenvalues, one corresponding to ‘house’ and one corresponding to ‘not-house’. The probability of each of these answers would be derived from the  geometry  of the space. N: You have lost me . . . again. Where do the concepts ‘house’ and ‘not- house’ come from? One minute we have an observable which corre- spondstoaqueryabout‘houseness’,nextwehaveconcepts,presumably represented in the space, how? K: Yes, that is right. I need to tell you about the idea of  eigenvectors . B: (With some despair) Oh no, not more algebra, is there no end to it? K: (Soothingly) We are almost there. Corresponding to each eigenvalue is an eigenvector. So, for a self-adjoint operator (that is, an observable) you get a number of eigenvectors corresponding to the concepts underlying the observable. It so happens that these eigenvectors make up a basis for the space and so generate a point of view.   It is as if we have found a set of concepts, one corresponding to each eigenvector, with respect to which we can observe each document in the space. B: What about this relationship between probability and the geometry of the space? K: I will come to that in a minute. N: (Somewhat grimly) I am glad to hear it, these algebraic considerations are starting to give me a headache. I thought all this was for IR? Anyway, proceed. K: For the simple case where the observable represents a Yes/No question, the linear operator is a particularly simple, and important one: a pro- jection operator. It is a theorem in linear algebra that any self-adjoint linear operator can be resolved into a linear combination of projec- tion operators. In other words, any observable can be resolved in to a combination of yes/no questions. Although a projector may be repre- sented by a matrix in  $n$   dimensions, it only has two eigenvalues. In gen- eral you would expect an  $n$  -dimensional matrix to have  $n$   eigenvalues.  

Projectors have two. The effect of this is that there is a certain amount of degeneracy, which means that corresponding to each eigenvalue we have an eigenspace, and together these two eigenspaces span the entire space.  

B: What about the basis? If the space is    $n$  -dimensional, we need    $n$   basis vectors to make up the basis.  

K: That is still so, except that within each subspace you can choose an arbitrary set of basis vectors spanning the  sub space. Adding these two sets will give a set of basis vectors spanning the whole space. This ﬁnishes the geometry.  

N: (Deliberately obtuse) What geometry? I only see vectors, subspaces, bases, and operators. Where is the geometry?  

You are right to be suspicious, the geometry is implied, and it is used to give us both a logic and a probability measure. To calculate the probability of a particular eigenvalue we project orthogonally the state- vector down onto its eigenspace and measure the size of that projection in some way to get the probability. Probability measures have to satisfy some simple constraints, like for example that the sum of the measures of mutually orthogonal subspaces, that together exhaust the space, must sum to one. The geometry of the space through Pythagoras’ Theorem ensures that this is indeed the case. Remember that theorem – (K quickly sketches it)  

![](images/753ef3d15e5df8be4d8823cd77a13b7a488f285b1ea39db01f03da4be3c4963a.jpg)  

B: So  $a^{2}$    has the value 1, where    $b^{2}$    and  $c^{2}$    are the measures of the corre- sponding subspaces. You slipped in the idea of probability rather neatly, but why should I accept that way of calculating probability as being use- ful, or meaningful? You seem to be simply replacing the inner product calculation with a probability. Why?  

K: A good question and a hard one. First let me emphasise that we use ‘probability’ because we ﬁnd it intuitive to talk of the probability that an object has a certain property, or that is about something. Of course, in quantum mechanics this is shorthand for saying that if one attempted to measure such a property or aboutness then a result would be returned with a probability, possibly with a probability of one or zero. The prob- lem is how to connect that probability with the geometric structure of  

the space in which the objects reside. I will need to develop the abstract view a little further before I can totally convince you that this is worth doing.  

N: Oh, no, not more mathematics. B: Perhaps you can give us little more intuition about how to make this connection between the geometry and probability. K: OK. But for further details I will have to refer you to a paper by William Wootters (1980a) and one by R. A. Fisher (1922), who were the ﬁrst to moot the intuition I am about to describe. In fact Wootters developed a simple example in a very different context, which I will follow trans- posed to an IR context. But ﬁrst let me go back to the pioneering work  

in the sixties. N: Yes, so he did, but as a model it never really took off, although the way of thinking in those early papers was very inﬂuential. K: I agree, and it will serve here to interpret how the probability arises out of the geometry. Imagine that a document is designed (by the author, artist, photographer, . . .) to transmit the information that it is about a cer- tain concept. One way to ascertain this information is to ask a large set of users to judge whether it is about that concept or not. A speciﬁc user answers either yes (Y) or no (N). Thus a long sequence, YNNYNY . . . , is obtained. We have assumed that our document is represented by a vector in a space, and that a concept is represented by a basis vector in the same space, the eigenvector of the observable representing the concept.   And so, geometrically, the extent to which that document is about the concept in question is given by the angle    $\theta$   the document vector makes with the concept vector. We assume (following Wootters) that we are able to ask the users indeﬁnitely, and that we cannot use the order in which the answers occur. You will agree that the probability,  $P$  , that a document is about the concept is given by the frequency of the Ys in the limit of the sequence, the size of sequence must not play a role. Now it turns out that the function  $P=\cos^{2}\theta$   is the best code for transmitting a   $\mathrm{Y}$   or  $\mathbf{N}$   in the sense of maximising information that will tell us what  $\theta$   is. One could describe this as a  content hypothesis : ‘The optimal way of displaying the content of a document in a vector space is to deﬁne the probability of a concept as the square of the modulus of projection of the state-vector on the concept vector’. This is a little  

more general than warranted by the example because it allows for com-  

N: Oh no, not another C-hypothesis, haven’t we already got enough of these? K: I am afraid not, I want to highlight that the connection between the content and the vector is in the way of a hypothesis, which of course should be testable. Anyway, I now turn to the connection with logic. Earlier I said that the language I was proposing would handle logic and probability. It turns out that given the notion of subspace we now have, we can claim that the lattice of subspaces, where  meet  is the intersection, and  join  is the subspace containing the linear span of all the vectors in both subspaces, form a non-Boolean lattice which is equivalent to a non-classical logic. All this is spelt out in some detail in Chapter 5 of my book. This result was probably ﬁrst elaborated by Birkhoff and von Neumann (1936). In fact, von Neumann foresaw very early on the intimate connection between logic and probability when formulated in Hilbert space. Theoreticians in computing science have not shown much interest in this until very recently; for example, Engesser and Gabbay (2002) have been investigating belief revision in the context of quantum logics. In IR, we wish to go further and explore the connection between geometry, logic and probability. B: So what? You have a way of arranging the  subspaces  of a Hilbert space. And, just like the  subsets  of a set make up a Boolean lattice, which is isomorphic to a classical logic, we now have these subspaces and get a non-Boolean lattice and logic. Then what? K: Well, remember that a query may be represented as a subspace, in the simplest case a 1-dimensional subspace and therefore a vector, and that we would want to calculate the probability that the subspace induces on the entire space. N: Wow, you now want us to grasp the notion of a subspace inducing a probability on a space. Does it get any freakier? K: Yes. This is one of the ideas that quantum mechanics brings into play, namely, that the state-vector is a measure of the space, meaning that each subspace has a probability associated with it induced by the state- vector. This generalises. B: (Impatiently) How? K: For this we need to return to these observables that I spoke of. I told you about a particularly simple one that was a projection operator, that is one that is idempotent   $(\mathbf{P}^{2}=\mathbf{P}$  ) and self-adjoint   $\mathbf{P}^{*}=\mathbf{P}$  . It has the eigenvalues 1 and 0. Another way of looking at it is that it projects  

onto a subspace corresponding to eigenvalue 1, and that it and the complementary subspace corresponding to 0 span the space. Now it is perfectly easy to deﬁne a projector onto a 1-dimensional subspace, that is onto a ray, or onto the subspace that contains all the scalar multiples of a vector. In the Dirac notation this becomes especially easy to denote. If x is a unit vector then  $\mathbf{P}=|\underline{{\mathbf{X}}}\rangle\langle\underline{{\mathbf{X}}}|$  . 5   The point is that  $\mathbf{P}$   is a member of a dual space to the vector space. It is the dual space of self-adjoint linear operators.  

N: OK, now we have two spaces, the vector space and its dual. What good is that? K: It turns out that we can name things in the dual space more easily. For example, we can name the projector onto a vector x by    $\left|\underline{{\mathbf{X}}}\right\rangle\left\langle\underline{{\mathbf{X}}}\right|$  . We can name the projector onto the subspace spanned by x and y by  $\mathbf{P}\!=\!|\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{x}}}|+$   $\lvert\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}\rvert$  . In fact, any superposition of states or mixture of states can be named by an operator in the dual space through what is known as a density operator . I realise that I have gone a bit fast here, but I wanted to get the point where I can talk about density operators. B: It seems to me that you are now shifting your emphasis from the vector space to the space of operators, why? K: Well spotted, I am doing exactly that, and the reason is that I want to introduce you to Gleason’s Theorem. His theorem makes the important connection between geometry and probability that I have been alluding to. But, his theorem is expressed in terms of density operators. N: All right, but for heaven’s sake tell me quickly what a density operator is before I lose the thread completely. K: A density operator is a self-adjoint linear operator that belongs to a certain sub-class of self-adjoint operators (or if you like observables) such that its eigenvalues are positive and the  trace  of it is one. The trace of an operator is the sum of is eigenvalues. The technical deﬁnition is:  $\mathbf{D}$   is a density operator if  $\mathbf{D}$   is a trace class operator and   $\operatorname{tr}(\mathbf{D})=1$  . K: I can now give you Gleason’s Theorem, and I am afraid there is no easy or simple way to do this other than by giving the full and correct statement. So here it is: (Hughes, 1989) ‘Let  $\mu$   be any measure on the closed subspaces of a separable (real or complex) Hilbert space  $\mathbf{H}$   of dimension at least 3. There exists a positive self-adjoint operator    $\mathbf{D}$   of trace-class such that, for all closed subspaces of  $\mathbf{H}$  ,  $\mu(L)=\operatorname{tr}(\mathbf Ḋ \mathbf Ḋ P Ḍ _{L})$  .’ 6  

If    $\mu$   is a  probability  measure thus requiring that    $\mu(\mathbf{H})=1$  , then  $\operatorname{tr}(\mathbf{D})=1$  , that is,  $\mathbf{D}$   is a density operator. There are many versions of this theorem, this is the one given in Hughes.  

You had better say more about this, for this is about as opaque as it gets. I guess I would like to see how this will help us in designing an algorithm for retrieval.  

B: Yes, let’s have it. All this mumbo jumbo has got to be good for some- thing. Although, I must admit it is neat and I like the way you have encoded probability in the geometry.  

K: Is it that way round? In fact it is both ways round. If you start with  D , and  $\mathbf{P}_{L}$   the projection onto the subspace    $L$  , then is easy to show that  $\mu(L)$   is a probability measure. Gleason’s Theorem tells us that if we have a measure    $\mu$   on the subspaces then we can encode that measure as a linear operator (density operator) to calculate that probability through  $\ensuremath{\mathbf{tr}}(\ensuremath{\mathbf{D}}\ensuremath{\mathbf{P}}_{L})$  .  

K: Well it is a sort of ‘comfort theorem’ ensuring that if we assume that these probability judgments can be made then we can represent those judgements through an algebraic calculation. I suppose you could say it is a sort of representation theorem. Just like a classical logic can reﬂect the relationships between subsets, here we have relationships between subspaces reﬂected through an algebraic calculation.  

B: I am still not sure what extra we get through this theorem. How would you apply it?  

K: (Getting enthusiastic again) Now it gets more interesting. The simplest way of thinking of a density operator is as follows:  

#  $\mathbf{D}=a_{1}\mathbf{P}_{1}+\cdot\cdot\cdot+a_{n}\mathbf{P}_{n},$  

where the  $a_{\mathrm{i}}$   are weights such that    $\Sigma a_{i}=1$   and the  $\mathbf{P}_{i}$   are projections onto (for simplicity let us say) a 1-dimensional vector space, a ray, so that  $\mathbf{P}_{i}=|\underline{{\mathbf{x}_{i}}}\rangle\langle\underline{{\mathbf{x}_{i}}}|$   where   $\underline{{\mathbf{X}_{i}}}$   is a normalised vector. These vectors do not have to be mutually orthogonal. These vectors could represent concepts, that is, base vectors, in which case  $\mathbf{D}$   is a form of weighted query. Also, D  could represent a weighted mixture of documents like these in a cluster, or a path of documents through a space of documents like in ostensive retrieval. In all cases  $\ensuremath{\mathbf{tr}}(\ensuremath{\mathbf{D}}\ensuremath{\mathbf{P}}_{L})$   gives a probability value to the subspace  $L$  . If    $L$   is a 1-dimensional subspace, e.g.    $\mathbf{P}_{L}{=}\,\,|\underline{{\mathbf{y}}}\rangle\,\langle\underline{{\mathbf{y}}}|=\mathbf{P}_{y}$  , things become very simple indeed. That is (sorry about the algebra,  

I will scribble it on the whiteboard):  

$$
{\begin{array}{r l}&{\mu(L)=\operatorname{tr}[(a_{1}\mathbf{P}_{1}+\cdot\cdot+a_{n}\mathbf{P}_{n})|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}|]}\\ &{\qquad=\operatorname{tr}[(a_{1}|\underline{{\mathbf{x}}}_{1}\rangle\langle\underline{{\mathbf{x}}}_{1}|+\cdot\cdot+a_{n}|\underline{{\mathbf{x}}}_{n}\rangle\langle\underline{{\mathbf{x}}}_{n}|)|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}|]}\\ &{\qquad=a_{1}\operatorname{tr}[|\underline{{\mathbf{x}}}_{1}\rangle\langle\underline{{\mathbf{x}}}_{1}\mid\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}|]+\cdot\cdot\cdot+a_{n}\operatorname{tr}[|\underline{{\mathbf{x}}}_{n}\rangle\langle\underline{{\mathbf{x}}}_{n}\mid\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}|]}\\ &{\qquad=a_{1}\langle\underline{{\mathbf{x}}}_{1}\mid\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}\mid\underline{{\mathbf{x}}}_{1}\rangle+\cdot\cdot\cdot+a_{n}\langle\underline{{\mathbf{x}}}_{n}\mid\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}\mid\underline{{\mathbf{x}}}_{n}\rangle\qquad{\mathrm{(belief~me)}}}\\ &{\qquad=a_{1}|\langle\underline{{\mathbf{x}}}_{1}\mid\underline{{\mathbf{y}}}\rangle|^{2}+\cdot\cdot\cdot+a_{n}|\langle\underline{{\mathbf{x}}}_{n}\mid\underline{{\mathbf{y}}}\rangle|^{2}~{\mathrm{(using~complex~numbers)}},}\end{array}}
$$  

which in a real vector space is a weighted sum of the squares of cos    $\theta_{i}$  , where  $\theta_{i}$   is the angle that y makes with concept or vector  $i$  . This takes us right back to the intuition based on Maron’s probabilistic indexing. Very neat.  

N: But does it work?  

Well, as always that is a matter for experimentation. The nearest to demonstrating that it works was the work on the Ostensive Model by Campbell and Van Rijsbergen (1996). They had a primitive ad hoc form for this way of calculating the probabilities and using them to navigate the document space. The great thing is that we now have a formalism that allows us to reason sensibly about that underlying mechanism and it applies to objects or documents in any media. It is not text speciﬁc. No assumptions are made about the vectors in the space other then that they participate in the geometry and that they can be observed for answers in the way I have been explaining.  

[B and N are contemplating the algebra on the whiteboard gloomily] N: (Suddenly cheerful) Shall we have some coffee?  

# 1 Introduction  

This book is about underlying ideas and theory. It is about a way of looking, and it is about a formal language that can be used to describe the objects and processes in Information Retrieval. It is not about yet another model for IR, although perhaps some will want to ﬁnd such an interpretation in it.  

Why do we need another way of looking at things? There are some good reasons.  Firstly , although there are several IR models, for example vector space, probabilistic, logical to name the most important, they cannot be discussed within a single framework.   This book, The Geometry of Information Retrieval (GIR), is a ﬁrst attempt to construct a unifying framework.  Secondly , although many of us pay lip-service to the conceptual depth of some of the fundamental notions in IR such as relevance, we rarely analyse these notions formally to any bedrock. This is not because we are lazy, it is rather because our theoretical tools have made it very difﬁcult to do so. What follows will, it is hoped, aid such formal analysis. And  thirdly , there is a need to support the formal speciﬁcation or expression of IR processes so that we can formally reason about them. For example, we need to be able to lay down mathematical constructs that will direct us in the design of some new algorithms for IR. This is especially important if we wish to extend the boundaries of current research.  Finally , a fourth reason is that IR research has now embraced the analysis of objects in any medium, that is, text, image, audio, etc., and it has become apparent that existing IR models apply to all of these media. In other words, IR models are not media speciﬁc, but sometimes the language that we have used has implied that they are so restricted. Here is an attempt to formulate the foundations of IR in a formal way, and at a level of abstraction, so that the results apply to any object in any medium, and to a range of modes of interaction.  

We want to consider the way  relevance  can be discussed in the context of information spaces. We begin by thinking of an information space as an abstract space in which objects of interest are represented, and within which a user can interact through observation and measurement with objects. Later such a space will be a Hilbert space. For the moment we assume that the objects are documents, and that each document is represented by a vector of ﬁnite dimensions in the space.  

Relevance, like information, has proved to be a slippery notion. Convention- ally, an object (usually referred to as a document but it can be an image or a sound sequence, etc.) is thought of as relevant to a user’s information need, thus the ultimate arbiter of relevance is the user. Relevance is therefore a subjec- tive notion, and the relevance of a document will vary from user to user. Even though two users may submit the same query to an IR system, their assess- ments of which documents are relevant may differ. In fact the relevance of a document for one user will change as the user interacts with the system. One way of describing this is to assume that relevance depends on the state of the user, and that as the user acquires more information, his or her state changes, implying that a document, potentially relevant before an interaction, may not be so afterwards. Modelling this extremely complicated process has been part of the inspiration for the search for a formal basis for IR.  

For the most part, computing or estimating relevance has been handled quite simply. It is generally assumed that relevance is 2-valued, a document being either relevant or not. Algorithms and models were developed to estimate the probability of relevance of any document with respect to a user need. Most simply, this is done by assuming that a query can be a reasonable representation, or expression, of a user’s information need. A calculation is made estimat- ing the similarity of the query to a document reﬂecting the probability of its relevance. The probability of relevance is not conceived to be the same as the degree of relevance of the document, because relevance is 2-valued at every stage (Robertson, 1977). By ﬁnding the probability of relevance for each doc- ument it is implied that there is a residual probability of non-relevance for that document.  

Let us begin by visualising the assessment of relevance in a 2-dimensional space. In it each document is represented by a 2-dimensional vector. Of course the structure of the space could be ignored completely and we could simply assert that the position of one document close to another tells us nothing about potential relevance. We do not do so because IR has been extremely successful in exploiting spatial structure. We make the underlying assumption everywhere in this book that the geometry of the information space is signiﬁcant and can be exploited to enhance retrieval.  

So, the question that remains is how do we represent the idea of relevance in the structure of such spaces. The motivation comes from quantum mechanics, where the state of a system is represented by a vector, the  state vector , in a ﬁnite or inﬁnite dimensional Hilbert space.  Observables , that is quantities to be measured, are represented by self-adjoint linear operators which themselves are represented as matrices with respect to a given basis for the Hilbert space. The subtle thing is that a measurement of an observable gives a result which is one of the eigenvalues of the corresponding operator with a probability determined by the geometry of the space. In physics the interpretation 3   can be that the state vector of the system collapses onto the eigenvector of the operator correspond- ing to the resulting measured value, that is the corresponding eigenvalue.   This collapse ensures that if the measurement were repeated immediately then the same value (eigenvalue) would be measured with probability 1. What may be useful for IR about this interpretation is the way the geometric structure is exploited to associate probabilities with measurements. This is a view of mea- surement, which is quite general and can be applied to inﬁnite as well as ﬁnite systems.  

We want to apply the quantum theoretic way of looking at measurement to the ﬁnding of relevance in IR. We would initially be interested in  ﬁnite  sys- tems, although this could change when thinking about measurements applied to images. It is possibly not controversial to assume that relevance is an observ- able. It may be controversial to assume that it corresponds to a self-adjoint linear operator, or a Hermitian operator, acting on the space of objects – which we are going to assume is a Hilbert space. Instead of the conventional assumption that the observation of relevance results in one of two values, we can easily represent a multi-valued relevance observable by simply extending the number of differ- ent eigenvalues for the relevance operator. Let us call the operator  R . In the binary case there will be exactly two ei nvalues  $\lambda_{1}=1$  ,  $\uplambda_{2}=0$   corresponding to the result of measuring the value of  R  for any document.  

In a high-dimensional space  $n>2$  , the eigenvalues, if there are just two eigenvalues, are what is called degenerate, meaning that at least one of the eigenspaces corresponding to    $\lambda_{i}$   has dimension greater than 1. This is a slightly troublesome feature because it becomes difﬁcult to illustrate the ideas geomet- rically. If we take the simple example of a 3-dimensional Hilbert space – that is, each document is represented as a 3-dimensional vector, and we assume that relevance is 3-valued, then  $\mathbf{R}$   will have three distinct eigenvalues  $\lambda_{1}\neq\lambda_{2}\neq\lambda_{3}$  (that is, no degeneracy). To measure  R  for any document in this space is to get one of the values    $\lambda_{i}$   with a certain probability. Geometrically, we can illustrate thus:  

![](images/ef9d2348bc0362103c472774e0938d726cc781ddae3963d73e005f2525a10bcf.jpg)  

$\{\underline{{\mathbf{e}}}_{1},\,\underline{{\mathbf{e}}}_{2},\,\underline{{\mathbf{e}}}_{3}\}$   is an orthonormal basis for the 3-space. Let x be a unit vector representing a document, let  $\{\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2},\underline{{\mathbf{e}}}_{3}\}$   be the eigenvectors corresponding to the three different eigenvalues  $\lambda_{1}\neq\lambda_{2}\neq\lambda_{3}$  . If  $\underline{{\mathbf{x}}}=c_{1}\underline{{\mathbf{e}}}_{1}+c_{2}\underline{{\mathbf{e}}}_{2}+c_{3}\underline{{\mathbf{e}}}_{3}$   then quantum mechanics dictates that the probability that measuring  R  for   $\underline{{\mathbf{X}}}$   will result in  $\lambda_{1},\,\lambda_{2}$   or  $\lambda_{3}$   is given by    $|c_{1}|^{2},\;|c_{2}|^{2}$    or    $|c_{3}|^{2}$  , which by Pythagoras’ Theorem indeed sum to one. The obvious question to ask is why should we interpret things this way? The answer is quite technical and will emerge in the sequel, but ﬁrst an intuitive explanation will be given.  

We began by making the assumption that the observable  R  was representable by a Hermitian operator, or in matrix terms one for which the matrix is equal to its conjugate transpose. This is  not  an intuitive assumption. Fortunately there is a famous theorem from Gleason (Hughes, 1989, p. 147) which connects measures on the subspaces of a Hilbert space with Hermitian operators. The importance of the theorem is that it helps us interpret the geometric description; later in the book this connection will be made precise. If we assume that each subspace, in particular each 1-dimensional subspace corresponding to an individual doc- ument, can have a measure associated with it, then Gleason’s Theorem tells us that there is an algorithm based on a Hermitian operator that will consistently give that measure for each closed subspace. If that measure is a probability measure then the Hermitian operator will be one of an important kind, namely a  density operator . A deﬁnition and description of a density operator can be found in Appendix III and Chapter 6.  

This relationship is quite general; it connects a consistent probability assign- ment to documents in space with a self-adjoint linear operator on that space. In other words there is a density operator that for each subspace will give the probability measure of that subspace. Now accepting that relevance judgments (Maron, 1965) are a matter of probability, we have established that some of the most successful retrieval engines are based on attempts to estimate probability of relevance for each document. Thus it is reasonable to represent the observ- able relevance as a linear operator of the kind speciﬁed by Gleason’s Theorem. It is important to realise that we are by no means ruling out that the probabilities may be subjective, that is that each user, or even the same user in a different context, can hypothetically have a different probability assignment in mind. Without any further interaction we do not yet know what they are. The whole point of an IR system is to estimate (or compute) the probabilities. However, we are now in a position to reason about relevance as a ﬁrst class object, namely as an observable, as applied to the space of objects.  

The Hermitian operator beautifully encapsulates the uncertainty associated with relevance. If the relevance operator has    $k$   eigenvalues    $\lambda_{k}$  , then the proba- bility of observing  $\lambda_{k}$  , one of the relevance values, for any particular document  $\underline{{\mathbf{X}}}$   is given by the size of the projection of  $\underline{{\mathbf{X}}}$  onto the eigenspace corresponding to  $\lambda_{k}$  . The reason we have an eigenspace and not an eigenvector is because the eigenvalues may be  degenerate ,   more about that later. All this simpliﬁes enor- mously if the eigenvalues are non-degenerate, for relevance, since we usually have a bi-valued relevance, typically there will be two eigenvalues only, which means that we have two eigen spaces .  

The analysis we have given above can be applied to any observable, and providing that we are convinced that there is a probability measure reﬂecting consistently some uncertainty on the space of objects, we can represent that observable by a density operator. It brings with it the added bonus that the eigenvectors (eigenspaces) of a particular operator give a particular perspective on the information space. Since the eigenvectors of a density operator make up an orthonormal basis for the space, each observable and corresponding operator will generate its own basis. In the space all calculations are done with respect to a particular basis, and if the basis is different then of course the probabilities will be different. So we see how it can follow that a difference in a relevance operator can be reﬂected in the probabilities.  

A second, different observable, important in IR, and quite distinct from relevance is ‘aboutness’ (Sober, 1985, Bruza, 1993, Huibers, 1996). Philosoph- ically, it is not clear at all whether ‘aboutness’ is a well-deﬁned concept for IR, but we will simply assume that it is. It arises from an attempt to reason abstractly about the properties of documents and queries in terms of index terms.  

The approach taken in this book is that these objects like documents do  not have  or  possess  properties or attributes.   The properties represented by an index term exist by virtue of applying an observable to an object and thereby making a measurement resulting in a value. It is as if the properties emerge from an interacton. The simplest case would be for a single-term observable resulting in a  Yes  or  No  answer. We can consider a entire query to be an observable and its constituent index terms to be the possible results of a measurement. There are various abstract ways of modelling this. The important idea is that we do not assume objects to have the properties a priori. In discussing aboutness we come from the opposite direction from that of relevance. In the case of aboutness we come from the very concrete notion that index terms represent properties of documents, which we are making more abstract, whereas with relevance we have a very abstract notion that we are making more concrete. The result is that both relevance and aboutness can be analysed formally in the same abstract Hilbert space in a comparable way.  

One reason for looking at ‘aboutness’ with textual documents is that it may be obvious that an index term belongs to a document because it occurs in the document as a token and therefore can act as a semantics for it. But, consider an image, which may be represented by a bunch of signals, maybe mathematical functions, and their obvious properties such as for example spatial frequencies cannot be related simply to a semantics.   So, we need to tackle ‘aboutness’ differently and more abstractly, and our proposal is that properties are modelled as observables by self-adjoint linear operators which when applied to an object (image) produce results with probabilities depending on the geometry of the space within which the objects are represented.  

Having described how an aboutness operator can be handled just like a relevance operator, we can now face the problem of describing the nature of their interaction. One way of formally interpreting the IR problem is that our representation of the information need (via a query) is intended to reﬂect rel- evance as closely as possible. Thus, when we rank documents with respect to a query, ideally the ranking would be in decreasing order of probability of rel- evance (Robertson, 1977). But, in the case where relevance and aboutness are both represented as observables, ideally the observables would be the same. Of course, in practice, this is rarely the case, and so we are left with the situation where the eigenvectors for  R  and  A  (aboutness) are at an angle to each other.  

We can illustrate this situation in two dimensions:  

![](images/a44281c01cee701d025f44c0c59bb66fd1e5cd6541b3f4fef3516ebddc366162.jpg)  

$|t=1\rangle$  and    $|t=0\rangle$  are the two eigenvectors associated with  A , and    $|r=1\rangle$  and    $|r=0\rangle^{8}$    are those associated with  R . A document is represented by the vector   $\underline{{\mathbf{X}}}$  . (All the vectors are normalised, that is, of unit length.) If we have an inner product 9   on this space then the geometry dictates that    $\mathbf{R}\underline{{\mathbf{x}}}=1\underline{{\mathbf{x}}}$   with probability    $|\langle{\underline{{\mathbf{x}}}}|r=1\rangle|^{2}$    and    $\mathbf{Ax}\underline{{=}}\ 1\underline{{\mathbf{x}}}$   with probability    $\vert\langle{\underline{{\mathbf{x}}}}\vert t=1\rangle\vert^{2}$  .   These probabilities arise because we wish to interpret the inner product in this way. If the eigenvectors for these two observables were to coincide then of course the probabilities would be the same. This would mean that the probability of being about  $t$   would be the same as the probability of being relevant a priori. But once having observed that x is about  $t.$  , then the probability of its relevance would be 1 and its probability of non-relevance would be 0. This is the simple case.  

Now take the case where the eigenvectors are at an angle to each other. We still have the a-priori probabilities, but what if we observe x to be about    $t.$  , then a subsequent observation of its relevance will depend on two probabilities  $|\langle r=1|t=1\rangle|^{2}$    and    $|\langle{\underline{{\mathbf{x}}}}|t=1\rangle|^{2}$  . If we are in a real Hilbert space then these are simply the squares of the cosines of the corresponding angles.  

The really interesting effect occurs when we have the following sequence of observations:  $\mathbf{A}\rightarrow\mathbf{R}\rightarrow\mathbf{A}$  .  

![](images/19a5f0087f40e38da6f31b0fd62363fe40b49e2e11c05dc68bd511529dfc682d.jpg)  

In the above diagram we assume that a document (represented by a state vec- tor x) enters the observation box  A  at the left.  A  represents an observable which corresponds to the property of ‘aboutness’, and to be concrete, it corresponds to whether a document is about a particular term,    $t.$  , which might be a term such as, for example, ‘money’, ‘bank’, etc. One can view  A  as representing a question, which has the answer either yes or no. A measurement is made to establish whether x is about  $t$   or not, this is a yes or no decision. After that the observable  $\mathbf{R}$   is applied to x assuming that x is  not  about  t . Again a measurement is made to establish whether x is relevant or not, again a yes/no decision. Similarly this may be viewed as asking the question, ‘is x relevant?’ If the interaction between A  and  $\mathbf{R}$   was classical then any subsequent measurement of  $t$   should result in the same result as the ﬁrst measurement, namely, that the answer to the question ‘is x about  $t?$   is still no. However, in the representation developed in this book there is an interaction between  A  and  R  such that when  R  is measured after  A  a subsequent measurement of  A  can once again give either result. This depends on whether the observables  A  and  R  have different eigenbases or, to put it more pre- cisely, whether  A  and  R  commute. The assumption made here is that  A  and  R  do not necessarily commute, that is, determining the aboutness followed by deter- mining relevance, is not the same as determining relevance followed by about- ness. In mathematical terms the operators  A  and  R  do not commute:  $\mathbf{AR}\neq\mathbf{RA}$  . This simple example illustrates the basis for the  interaction protocol  $l^{11}$    we pro- pose between users and information spaces, leading to the development of what one might term an  interaction logic  for IR.  

Here is a simple example of two non-commuting observables represented by their corresponding matrices.  

$$
{\begin{array}{r l}{\mathrm{A}={\left(\begin{array}{l l}{0}&{1}\\ {1}&{0}\end{array}\right)}}&{\mathrm{R}={\left(\begin{array}{l l}{1}&{0}\\ {0}&{-1}\end{array}\right)}}\\ {\mathrm{AR}={\left(\begin{array}{l l}{0}&{-1}\\ {1}&{0}\end{array}\right)}}\\ {\mathrm{RA}={\left(\begin{array}{l l}{0}&{1}\\ {-1}&{0}\end{array}\right)}}\\ {\mathrm{AR}\neq\mathrm{AR}.}\end{array}}
$$  

We can extend this analysis to the interaction between different index terms. It is usual and convenient in IR to assume that index terms are independent. In the geometrical picture being described, term independence means that separate observables corresponding to the different terms will commute. If they are not independent then the 2-dimensional eigenbases are different for each term, the angle between each pair of bases reﬂecting the dependence. In fact it is conve- nient to assume that a query operator has a set of eigenvectors as a basis, each vector corresponding to a concept and independent from each other concept. This is very similar to the representation adopted by Latent Semantic Indexing (Deerwester  et al ., 1990).  

The foregoing has given a simple description of the conceptual basis of what we describe mathematically in the chapters that follow. This just leaves me to explain the general approach and structure of the rest of the book. A quote from John von Neumann to some extent expresses the spirit of the endeavour. Of course he was talking about quantum mechanics and not information retrieval. I quote at length with grammatical mistakes and all (R´ edei and St¨ oltzner, 2001, pp. 244–245): 13  

If you take a classical mechanism of logics, and if you exclude all those traits of logics which are difﬁcult and where all the deep questions of the foundations come in, so if you limit yourself to logics referred to a ﬁnite set, it is perfectly clear that logics in that range is equivalent to the theory of all sub-sets of that ﬁnite set, and that probability means that you have attributed weights to single points, that you can attribute a probability to each event, which means essentially that the logical treatment corresponds to set theory in that domain and that a probabilistic treatment corresponds to introducing measure. I am, of course, taking both things now in the completely trivialized ﬁnite case.  

But it is quite possible to extend this to the usual inﬁnite sets. And one also has this parallelism that logics corresponds to set theory and probability theory corresponds to measure theory and that given a system of logics, so given a system of sets, if all is right, you can introduce measures, you can introduce probability and you can always do it in very many different ways.  

In the quantum mechanical machinery the situation is quite different. Namely instead of the sets use the linear sub-sets of a suitable space, say of a Hilbert space. The set theoretical situation of logics is replaced by the machinery of projective geometry, which in itself is quite simple.  

However, all quantum mechanical probabilities are deﬁned by inner products of vectors. Essentially if a state of a system is given by one vector, the transition probability in another state is the inner product of the two which is the square of the cosine of the angle between them. In other words, probability corresponds precisely to introducing the angles geometrically. Furthermore, there is only one way to introduce it. The more so because in the quantum mechanical machinery the negation of a statement, so the negation of a statement which is represented by a linear set of vectors, corresponds to the orthogonal complement of this linear space .  

And therefore, as soon as you have introduced into the projective geometry the ordinary machinery of logics, you must have introduced the concept of  

orthogonality. This actually is rigorously true and any axiomatic elaboration of the subject bears it out. So in order to have logics you need in this set of projective geometry with a concept of orthogonality in it.  

In order to have probability all you need is a concept of all angles, I mean angles other than  $90^{\circ}$  . Now it is perfectly quite true that in a geometry, as soon as you can deﬁne the right angle, you can deﬁne all angles. Another way to put it is that if you take the case of an orthogonal space, those mappings of this space on itself, which leave orthogonality intact, leave all angles intact, in other words, in those systems which can be used as models of the logical background for quantum theory, it is true that as soon as all the ordinary concepts of logics are ﬁxed under some isomorphic transformation, all of probability theory is already ﬁxed.  

What I now say is not more profound than saying that the concept of a priori probability in quantum mechanics is uniquely given from the start. You can derive it by counting states and all the ambiguities which are attached to it in classical theories have disappeared. This means, however, that one has a formal mechanism, in which logics and probability theory arise simultaneously and are derived simultaneously. I think that it is quite important and will probably [shed] a great deal of new light on logics and probably alter the whole formal structure of logics considerably, if one succeeds in deriving this system from ﬁrst principles, in other words from a suitable set of axioms. All the existing axiomatisations of this system are unsatisfactory in this sense, that they bring in quite arbitrarily algebraical laws which are not clearly related to anything that one believes to be true or that one has observed in quantum theory to be true. So, while one has very satisfactorily formalistic foundations of projective geometry of some inﬁnite generalizations of it, of generalizations of it including orthogonality, including angles, none of them are derived from intuitively plausible ﬁrst principles in the manner in which axiomatisations in other areas are.  

(John von Neumann, 1954.)  

The above is a pretty good summary of how by starting with simple set theory to model retrieval we are progressively pushed into more structure on the set of objects, which brings with it different logics and theories of probability. In the end we have a representation where objects are embedded in Hilbert space, observations are achieved by applying linear operators to objects as vectors. The logic is determined by the collection of linear subspaces and a probability measure is generated through a consistent measure on the set of linear subspace s, as speciﬁed by Gleason’s Theorem (Gleason, 1957).  

Before proceeding to the next chapter it may be useful to highlight two technical issues which will have profound implications for any attempts to develop further this theoretical approach. The ﬁrst is concerned with the use of complex numbers (Accardi and Fedullo, 1982). In what follows there is no restriction placed on the scalars for the Hilbert space. In other words in general we assume all scalars to be complex numbers of which the reals are a special case. For example, the complex combination of two vectors  $\underline{{\mathbf{X}}}$   and y giving rise to    $\alpha_{-}\tt_{+}+\beta_{-}$  , where    $\alpha$   and    $\beta$   are complex numbers, is allowed. Now it is not immediately obvious how this use should be interpreted or indeed exploited. The thing to realise is that it is a question of  representation . In the entire theory that follows, the  results  of measurements are and always will be real. That is, even if a document is represented by a vector in a complex space, the result of applying a linear self-adjoint operator to it, whose matrix entries may be complex, will give rise to a real with a given probability. Thus, although the representation is in terms of complex numbers, the result of an interaction is always real. For text retrieval this may prove useful if we wish, for example, to use both term frequency and document frequency associated with a given term as part of a matching algorithm expressed as an operation in Hilbert space. Thus if  $t f$   is the term frequency and we use  idf  to represent the document frequency, then this information can be carried by a complex number    $c$  , where  $c=i d f+\mathrm{i}t f$  . 15   In this way the identity of the two different frequencies could be preserved until some later stage in the computation when an explicit instruction is carried out to combine the two into a real number (or weight). How to do this explicitly is not clear yet, but there is no need to cut off the generality provided by complex numbers. Of course, when the objects represent images we have absolutely no idea what the best representation is and it may be that in the same way as we need complex numbers when we do Fourier transforms of signals, when specifying operations on images we may ﬁnd a use for the extra representation power afforded by complex numbers.  

This leaves us with the intriguing question of the inherent nature of the probability that we have developed here following the lines in which it is used in quantum mechanics. Traditionally, probabilities are speciﬁed as measures on sets, and if the sets are subsets of a multi-dimensional space they have the properties of volume. Thus, the volume of subset    $V_{i}$   is given as a relative volume with respect to the entire set’s volume    $V$   by    $\left|V_{i}\right|/\left|V\right|$  .   The volume numbers behave like relative frequencies, and indeed two disjoint (relative) volumes can be added to give the relative volume of the union. This is all familiar, for example see any standard text on probability such as Feller (1957), and the Kolmogorov axioms (see his book, 1950) capture this kind of probability very neatly.  

In quantum mechanics things are different and the basis for the probability assignment is Pythagoras’ Theorem. In the diagram below   $\underline{{\mathbf{X}}}$   and  $\underline{{\boldsymbol{\mathrm{y}}}}$   are the eigenvectors of an observable  A , and make up a 2-dimensional orthonormal basis for a 2-dimensional space. The projection of    $c$   onto   $\underline{{\mathbf{X}}}$   is    $a$  , and    $b$   is the projection of    $c$   onto y. In two dimensions we have  

![](images/41ac0fd540bdbe1482060d8b2b00c21eaf820944d5039167741b28d44f8a6894.jpg)  

and we all know that  

$$
\begin{array}{r l}{a^{2}+b^{2}}&{=c^{2}}\\ {\left({\frac{a}{c}}\right)^{2}+\left({\frac{b}{c}}\right)^{2}}&{=1}\\ {{\mathrm{or}}\quad\cos^{2}\theta+\cos^{2}\varphi\ =1,\quad0\leq\cos\theta\leq1,\quad0\leq\cos\varphi\leq1.}\end{array}
$$  

This gives a way of interpreting a probability of observing the result of an observable  A  with two outcomes  $a_{1},a_{2}$  , where  $a_{1}$   is the eigenvalue correspond- ing to the eigenvector  $\underline{{\mathbf{X}}}$  , and  $a_{2}$   is the eigenvalue corresponding to the eigenvec- tor y. In our earlier discussion  $a_{1}$   would represent yes and  $a_{2}$   would represent no to a question represented by  A . The state of the system (or the document) is represented by the vector s, and if normalised its length    $c=1$  . So we can assign a probability  $p_{1}$   to be the probability that we get    $a_{1}$   for observable  A s, where  $p_{1}=\operatorname{Prob}(\mathbf{A}=a_{1}|\ \underline{{\operatorname{s}}})=\cos^{2}\theta$   and  $p_{2}=\mathrm{Prob}(\mathbf{A}=$   $a_{2}|\ {\underline{{\mathbf{s}}}})=\cos^{2}\varphi$  |  = . The state s can vary throughout the space but  $p_{1}+p_{2}=1$   for any s. In particular  $p_{1}=1$   and  $p_{2}=0$  , if   $\underline{{\boldsymbol{\mathrm{S}}}}$   lies along   $\underline{{\mathbf{X}}}$   and vice versa if  $\underline{{\boldsymbol{\mathrm{S}}}}$   lies along y.  

This way of assigning probabilities generalises readily to    $n$   dimensions, indeed to inﬁnite dimensions, and handles complex numbers without any dif- ﬁculty. In one sentence, we can summarise the purpose of this book by saying that it is an attempt to show that this kind of probability assignment in Hilbert space is a suitable way of describing interaction for information retrieval.  

# Further reading  

There are now some good introductions to information retrieval that cover the foundations of the subject from different points of view. The most recent is Belew (2000) which takes a cognitive perspective. A more traditional approach is taken by Kowalski and Maybury (2000), and Korfhage (1997). The texts by Baeza-Yates and Ribeiro-Neto (1999), and Frakes and Baeza-Yates (1992) emphasise algorithmic and implementation issues. Before these more recent textbooks were published, one was mostly dependent on research monographs, such as Fairthorne (1961), Salton (1968) and Van Rijsbergen (1979a). These are worth consulting since many of the research ideas presented in them are still of current interest. The monograph by Blair (1990) is unique for its emphasis on the philosophical foundations of IR. Dominich (2001) has given a very mathematical account of the foundations of IR. In Sparck Jones and Willett (1997) one will ﬁnd a collection of some of classic papers in IR, to this it is worth adding the paper by Fairthorne (1958) which is perhaps one of the earliest paper on IR ever published in the computer science literature. A still much cited text book is Salton and McGill (1983) as it contains a useful elementary introduction to the vector space approach to IR.  

The main body of this book draws heavily on the mathematics used in quan- tum mechanics. The preceding chapter makes clear that the motivation for viewing and modelling IR formally in the special way just described is also drawn from quantum mechanics. To gain a better understanding of quantum mechanics and the way it uses the appropriate mathematics one can consult a number of introductory (sometimes popular) texts. The bibliography lists sev- eral, together with annotations indicating their relevance and signiﬁcance. One of the simplest and clearest popular introductions is Albert (1994), which does not shy away from using the appropriate mathematics when needed, but always gives an intuitive explanation of its use.   An excellent and classical account of the mathematical foundations is Jauch (1968), he also in 1973 published a delightful dialogue on the reality of quanta. For the philosophically minded, Barrett (1999) is worth reading. There are several good popular introductions to quantum mechanics, for example Penrose (1989, 1994), Polkinghorne (1986, 2002),Rae(1986).Wick(1995)isawell-writtensemi-popularaccount,whereas Gibbins (1987) contains a nice potted history of QM before dealing with the paradoxes of QM as Wick does. A useful dictionary, or glossary, of the well known terms in QM can be found in Gribbin (2002). There are many more entries in the annotated bibliography at the end of the book, and it may be worth scanning and reading the entries if one wishes to tackle some of the more technical literature before proceeding to the rest of this book.  

18  It is also good for getting acquainted with the Dirac notation.  

#  

# On sets and kinds for IR  

In this chapter an elementary introduction to simple information retrieval is given using set theory. We show how the set-theoretic approach leads natu- rally to a Boolean algebra which formally captures Boolean retrieval (Blair, 1990). We then move onto to assume a slightly more elaborate class structure, which naturally leads to an algebra which is non-Boolean and hence reﬂects a non-Boolean logic (see Aerts  et al ., 1993, for a concrete example). The chap- ter ﬁnishes by giving a simple example in Hilbert space of the failure of the distribution law in logic.  

# Elementary IR  

We will begin with a set of objects; these objects are usually documents. A document may have a ﬁner-grained structure, that is, it may contain some structured text, some images and some speech. For the moment we will not be concerned with that internal structure. We will only make the assumption that for each document it is possible to decide whether a particular attribute or property applies to it. For example, for a text, we can decide whether it is about ‘politics’ or not; for images we might be able to decide that an image is about ‘churches’. For human beings such decisions are relatively easy to make, for machines, unfortunately, it is very much harder. Traditionally in IR the process of deciding is known as indexing, or the assigning of index terms, or keywords. We will assume that this process is unproblematic until later in the book when we will discuss it in more detail. Thus we have a set of attributes, or properties (index terms, keywords) that apply to, or are true of, an object, or not, as the case may be. Formally the attributes may be thought of as predicates, and the objects for which a predicate is true are said to  satisfy that predicate. Given a set of objects    $\{x,y,z,\,.\,.\,.\}=\Omega$   and a set of predicates  $\{P,\,Q,\,R,\,.\,\.\,\.\}$   we can now illustrate a simple model for IR using na¨ ıve set theory.  

Picture    $\Omega$   as a set thus:  

![](images/4d5172011de718fc4e061b335b54134539bee4f6dd1a90f7b614e4313c545694.jpg)  

we can describe the set of objects that satisfy  $P$   as   $\mathbb{\{P}}\mathbb{\}=\{x\mid P(x)$   =  {  | ) is true } and the set of objects satisfying  $Q$   as  $\left\|Q\right\|=\left\{x\mid Q(x)\right.$   =  {  | ) is true } . This notation is rather cumbersome and usually, in the diagram, and discussion,   $\left[\![P]\!\right]$  ] is simply referred to as    $P$  , that is the set of of objects satisfying a predicate    $P$   is also referred to as    $P$  . There is a well-known justiﬁcation for being able to make this identiﬁcation which is known as the Stone Representation Theorem (see Marciszewski, 1981, p. 9). Hence given any subset in the set    $\Omega$   it represents a property shared by all the objects in the subset. That in general we can do this in set theory is known as the ‘comprehension axiom’, a detailed deﬁnition and discussion can be found in Marciszewski.  

Now with this basic set-up we can specify and formulate some simple retrieval. We can ask the question    $\{x\mid P(x)$   is true } , that is we can request to retrieve all objects that satisfy  $P$  . Similarly, we can request to retrieve all objects that satisfy  $Q$  . How this is done is a non-trivial issue of implementation about which little will be said in this book (but see  Managing Gigabytes  by Witten  et al ., 1994). The next obvious step is to consider retrieving all objects that satisfy both  $P$   and    $Q$  , that is,  

$$
\begin{array}{r}{\{P\land Q\}=\{x\mid{}^{\cdot}P(x)\,\mathrm{is~true}^{\prime}\,\mathrm{and}\,^{\cdot}Q(x)\,\mathrm{is~true}^{\prime}\}.}\end{array}
$$  

Here we have slipped in the predicate    $P\land Q$  , whose meaning (or extension) is given by the intersections of the sets satisfying    $P$   and    $Q$  . In other words we have extended the language of predicates to allow connectives. Similarly, we can deﬁne  

$$
\{\![P\lor Q]\!\}=\{x\mid{}^{\cdot}P(x)\,{\mathrm{is~true}}^{\prime}\,{\mathrm{or}}\,\,^{\cdot}Q(x)\,{\mathrm{is~true}}^{\prime}\}
$$  

and  

#  $\left[\!\!\left[\neg Q\right]\!\!\right]=\left\{x\mid$  ¬  = {  |  It is not the case that ‘  $Q(x)$   is true’ } .  

What we have now is a formal language of basic predicates and simple logical connectives  $\wedge$  (and),    $\vee$  (or) and  ¬  (not). The meaning of any expression in that language, for example   $(P\land Q)\lor(\neg R)$  , is given by the set-theoretic operations on the ‘meaning’ of the individual predicates. That is  

$$
\begin{array}{r}{\![P\land Q]\!]=\mathbb{[P]}\cap\mathbb{[Q]},}\end{array}
$$  

$$
\left[\!\left[P\vee Q\right]\!\right]=\left[\!\left[P\right]\!\right]\cup\left[\!\left[Q\right]\!\right]
$$  

$$
\begin{array}{r}{\left\[\neg P\right]\!\!\right\}=\Omega-\left\{\left[P\right]\!\!\right\},}\end{array}
$$  

and where   $\left.\varsigma\right\rrangle$   is set intersection, ‘ ∪ ’ is set union, and ‘ − ’ is set complementa- tion. Hence  

$$
\ensuremath{\mathbb{I}(P\wedge Q)}\vee\neg R\ensuremath{\mathbb{I}}=(\ensuremath{\mathbb{P}}\ensuremath{\mathbb{I}})\cap\ensuremath{\mathbb{I}}\ensuremath{\mathbb{Q}}\ensuremath{\mathbb{I}}))\cup\ensuremath{\mathbb{I}}\neg R\ensuremath{\mathbb{I}}.
$$  

The fact that we can do this thus, that is make up the meaning of an expression in terms of the meanings of the component expressions, without taking into account the context, is known as the Principle of Compositional it y. (Dowty et al ., 1981, Thomason,1974).  

In retrieval terms, if a query    $Q$   is given by   $(R\wedge B)\wedge\neg M,$  , where  

$$
\begin{array}{l}{R=\mathrm{trivers}}\\ {B=\mathrm{banks}}\\ {M=\mathrm{money},}\end{array}
$$  

then    $Q$   is a request for information for documents about ‘river banks’ and not about ‘money’. It amounts to requesting the set   $[\![Q]\!]$  ] given by    $\{x\mid Q(x)$   is true } , that is we are looking for the set of all  $x$   where each  $x$   satisﬁes  $P$   and    $Q$   but not  $M.$  . Pictorially it looks like this:  

![](images/9fccf03c6315986acb32c978ab26a423f4312434a2927c6683e2918df7cbe189.jpg)  

What has been described so far are the basics of Boolean retrieval (Kowalski and Maybury, 2000, Korfhage, 1997). ‘Boolean’ because the logic used to express the retrieval request, such as Q, is Boolean (Marciszewski, 1981).  

The beauty of this approach is that we do not have to say anything about the structure of the set    $\Omega$  . There is no information about whether an object  $x$   is similar or dissimilar to an object  y . The only information that is used is whether an object  $x$   possesses a predicate    $P$  , whether any two objects share a predicate  $P$  , and whether the same objects satisfy one or more predicates. 1   We need to know no more, we simply have to be able to name the objects    $\{x,y,z,\cdot\cdot.\}$   and be able to decide whether any predicate (attribute)    $\{P,Q,R,.\ .\ .\}$   applies to it.  

Unfortunately experience and experiment have shown that IR based on this simple model does not deliver the required performance (Blair, 1990). The performance of a retrieval system is usually deﬁned in terms of the ability to retrieve the ‘relevant’ objects (precision) whilst at the same time retrieving as few of the ‘non-relevant’ ones as possible (recall).   This is not a simple issue. There is a vast literature on what determines a relevant and a non-relevant object (Saracevic, 1975, Mizzaro, 1997). We return to aspects of this decision-making later. What is worth saying here is that it is not straightforward to formulate a request such as    $Q$   and to retrieve   $[\![Q]\!]$  ]. There is no guarantee that   $[\![Q]\!]$  ] will contain all the relevant objects and only the relevant ones, that is, no non- relevant ones. Typically   $\left[\![Q]\!\right]\!$  ] will contain some of each. The challenge is to deﬁne retrieval strategies that will enable a user to formulate and reformulate  $Q$   so that the content of   $[\![Q]\!]$  ] is optimal.  

In order to introduce the standard effectiveness measures of retrieval we are required to extend the structure of the set    $\Omega$   with the counting measure, so that we can tell what the size of each subset is. If we assume that the subset of relevant documents in    $\Omega$   is  $A$  , then the number of relevant documents is given by  $|A|$  , where    $\left|\cdot\right|$   is the counting measure. The most popular and commonly used effectiveness measures are  precision  and  recall . In set-theoretic terms, if    $B$   is the set of retrieved documents then  

$$
{\mathrm{precision}}=|A\cap B|/|B|,{\mathrm{and}}\;{\mathrm{recall}}=|A\cap B|/|A|.
$$  

A well-known composite effectiveness measure is the E-measure; 3   a special case is given by  

$$
E=|A\,\Delta\,B|/(|A|+|B|)=(|A\cup B|-|A\cap B|)/(|A|+|B|),
$$  

where    $\Delta$   is known as the symmetric difference.   It calculates the differ- ence between the union and intersection of two sets. Another special case is  $F=1-E$  , w ch is ow commonly used instead of  $E$   when measuring effec- tiveness. Both  E  and  F  can be expressed in terms of precision and recall.  

It is tempting to generalise the counting measure  $\left|\cdot\right|$   to some general (prob- abilistic) measure, but at this stage there are no grounds for doing that (but see Van Rijsbergen, 1979b). Beyond being able to tell what size a set is, unless we know more about the detailed structure of each object in    $\Omega$  , we cannot say much more.  

Returning to our general set-theoretic discussion about the correspondence between subsets and predicates, it would appear that  $A$   and  $B$   are the extension of predicates, properties attributable to the members of A and B. With a thorough abuse of notation one might express this as  $A=$  [ [relevant] ] and  $B=\mid$  [retrieved] ]. However, they are strange predicates because they are not known in advance. Let us take the predicate  retrieved  ﬁrst. This is usually speciﬁed algorithmically, and indeed in the case of Boolean retrieval is the set satisfying a Boolean expression  $Q$  , whatever that may turn out to be. The second predicate  relevance  is user dependent, because only a user can determine whether an object  $x\!\in\!\Omega$   isrelevant to her or his information need. The impression given by the deﬁnitions of precision and recall is slightly misleading because they appear to have asserted that the set  $A$   is known in advance and static, neither of which in practice is the case. As a ﬁrst approximation in designing models and implementations for IR we assume that such a set exists and can be found by generating a series of subsets  $B_{i}$   which together will somehow end up containing  $A$  , the set of all relevant documents. That is, a user attempts to construct  $\cup_{i}B_{i}$   such that  $A\subseteq\cup_{i}B_{i}$  . This process can be broken down into a number of steps such that    $|A\cap B_{i}|$   is as large as possible and  $B_{i}\neq B_{j}$  , so that at each stag  new members of  $A$   may be found. Unfortunately, without a ﬁle-structure on    it is difﬁcult to see how to guide a user towards the discovery of  $A$  . Of course each  $B_{i}$   may give hints as to how to formulate the next  $Q_{i+1}$   corresponding to    $B_{i+1}$   but such a process is fairly random.  

What is more interesting is to consider the interaction between the various predicates. Let us concentrate on the two kinds, one to connect with ‘aboutness’, these predicates I have called    $\{P,Q,R,\ldots\}$  ; and the kind for ‘relevance’ which for convenience I will call predicate  $X$  . We will consider how the observation of one predicate followed by the observation of another may affect the judgement about the ﬁrst. Perhaps it would be best to begin with a simple example. Let    $Q$  stands for ‘banks’, that is  

$$
\left\{\left[Q\right]\right\}=\left\{x\mid x{\mathrm{~is~about~banks}}\right\}
$$  

4  This is like a Hamming distance for sets.  

and  

$$
\mathbb{[}\neg Q\mathbb{]}=\{x\mid x{\mathrm{~is~not~above}}\}.
$$  

In our set-theoretic account we have assumed that ‘aboutness’ is a bivalent property, that is  

$$
x\in\left[\!\left\lfloor Q\right\rfloor\!\right]{\mathrm{~or~}}x\in\left[\!\left\lfloor\neg Q\right\rfloor\!\right]{\mathrm{~for~all~}}x\in\Omega.
$$  

Many models for IR assume this,   they assume that whether an object is about  $Q$   or not  $Q$   can be established objectively once and for all by some computation. This assumption may be challenged, and in fact it is more natural to assume that an object is about neither, or both, until an observation by a user forces it to be about one or the other, from the point of view of the user.  

Now let us bring predicate  $X$   (relevance) into play. Once object    $x$   has been observed to be about banks   $(Q)$   and the relevance is established, a subsequent repeat observation of whether  $x$   is about banks may lead to a different result. The intuitive explanation is that some cognitive activity has taken place between the two observations of  $Q$   that will change the state of the observer from one mea- surement moment to the next (see for example Borland, 2000, p. 25).   The same phenomenon can occur when two aboutness predicates  $P$   and  $Q$   are observed in succession. The traditional view is that we can treat  $P$   and  $Q$   independently and that the observation of  $P$   followed by  $Q$   will not affect the subsequent observa- tion of  $P$  . Once again observing    $Q$   in between two observations of    $P$   involves some cognitive activity and may have an effect. Of course we are assuming here that aboutness, like relevance, is established through the interaction between the user and the object under observation.  

What we have described above is a notion of  compatibility  between predi- cates or subsets. Technically, this can be expressed as  

$$
P=(P\land Q)\lor(P\lor\lnot Q),
$$  

when  $P$   and    $Q$   are compatible, or  

$$
X=(X\wedge Q)\vee(X\vee\neg Q),
$$  

where  $X$   is the relevance predicate. In the latter case, if    $Q$   stands for a sim- ple index term like ‘banks’, then the expression means that relevance can be separated into two distinct properties ‘relevance and bankness’ and ‘relevance and non-bankness’. When predicates are incompatible the relationship does not hold. There is a well known law of logic,  distribution , which enables us to rewrite  $X$   as follows:  

$X=(X\wedge Q)\vee(X\wedge\neg Q)=X\wedge(Q\vee\neg Q)$  

In our Boolean model the distributive law holds, and all predicates (subsets) are treated as compatible. If, on the other hand, we wish to model a possible incompatibility between predicates, because of interaction, then the Boolean Model is too strong, because it forces compatibility.  

Before moving on to other structures there is one more aspect of the set- theoretic (Boolean) approach that needs to be clariﬁed. One of the most difﬁcult things in modelling IR is to deal with the interplay between sets, measures and logic. The element of logic that is central, and most troublesome, is the notion of implication. In Boolean logic the connective   $\hookrightarrow'$   is deﬁned for two propositions  $A$   and  $B$   by setting  $A\to B=\neg A\lor B$  . Using the notation introduced earlier, the semantics may be given as  

$$
\![\![A\to B]\!]=\{x|x\in[\![\neg A]\!]\cup[\![B]\!]\}.
$$  

This connective is important because it enables us to perform inference. For us to prove an implication such as  $A\rightarrow B$   it sufﬁces to deduce the consequent    $B$  from the antecedent (according to some ﬁxed rules). This can be strengthened into a full-blown Deduction Theorem that for classical logic states  

$$
A\wedge B\vDash C{\mathrm{~if~and~only~if~}}A\vDash B\to C;
$$  

in words this says that if    $C$   is semantically entailed by  $A$   and  $B$  , then  $A$   semanti- cally entails  $B\rightarrow C.$  , and if  $A$   semantically entails  $B\rightarrow C$   then    $C$   is semantically entailed by  $A$   and  $B$  . Of course  $A$   may be empty, in which case we have  

$$
B\models C{\mathrm{~if~and~only~if~}}\models B\rightarrow C.
$$  

Much of classical inference is based on this result.When later we introduce more structure into our object space    $\Omega$   we will discover that the lack of distribution in the logic means we have to sacriﬁce the full-blown Deduction Theorem but retain its special case.  

We now move on from considering just sets, subsets, and the relationships between them to a slightly more elaborated class structure, which inevitably leads to a non-boolean logic. We motivate this class structure by ﬁrst looking at a primitive form of it, namely, an inverted ﬁle, which itself is used heavily in IR.  

# Inverted ﬁles and natural kinds  

Inverted ﬁles have been used in information retrieval almost since the very beginning of the subject (Fairthorne, 1958). Most introductions to IR contain a detailed description and deﬁnition of this ﬁle-structure (see for example Van Rijsbergen, 1979a, Salton and McGill, 1983 and Witten  et al ., 1994). Here we use it in order to motivate a discussion about classes of objects, their properties and their associated kinds. In particular we demonstrate how these considera- tions lead to a weak logic that is not distributive and of course, therefore, not Boolean. All we need for our discussion is classes of objects taken from    $\Omega$   and a notion of attribute, property or trait associated with objects. To begin with we must determine whether objects share attributes in common or not. The kind of class  $S$   that will interest us is one where the members share a number of attributes and only those attributes. Thus any object not in  $S$   does not share all the properties. At the most primitive level this is true of the buckets of an inverted ﬁle. For example, the class of objects about mammals is indexed by ‘mammals’ and the inverted ﬁle will have a bucket (a class!) containing all and only those objects indexed by ‘mammals’. Similarly, ‘predators’ indexes the class of objects about predators. These classes may of course overlap, an object may be indexed by more than one attribute.  

# Deﬁnition D1 9  

A set    $T$   of attributes  determine  a set  $A$   of individuals if and only if the following conditions are satisﬁed:  

(1) every individual in  $A$   instantiates  every attribute in    $T$  ;

 (2) no individual not in  $A$   instantiates  every attribute in    $T$  .  

If  $T$   is a singleton set then the  $A s$   are the buckets of an inverted ﬁle.  

# Deﬁnition D2  

A set of individuals is an  artiﬁcial  class if there is a corresponding set   $\operatorname{tr}(A)$   of attributes that determine  $A$  .  

9  The formal treatment that follows owes much to Hardegree (1982).  

Please notice that we are using a contrary terminology from the philosophical literature (Quine, 1969, Lakoff, 1987) by deﬁning artiﬁcial classes instead of natural classes. We prefer to follow the  Numerical Taxonomy  literature (Sneath and Sokal, 1973, p. 20).  

Formally, we can deﬁne the attributes of a class  $A$   and the individual instan- tiating the attributes as follows (where  $V$   is the set of possible attributes, and    $\Omega$  the universe of objects).  

# Deﬁnition D3  

$$
\operatorname{tr}(A)=\{t\in V\mid a\,\Delta\,t\,{\mathrm{for~all}}\,a\in A\}.
$$  

# Deﬁnition D4  

$$
\operatorname{in}(T)=\{a\in\Omega\mid a\,\Delta\,t\,\mathrm{for}\,\,\mathrm{all}\,\,t\in T\},
$$  

where    $\Delta$   is a relation on    $\Omega\!\times\!V!$  , the cross product of the universe of objects with the universe of attributes.  

Let us consider an example:  

(1)    $H$   is the set of objects about humans;

 (2)    $L$   is the set of objects about lizards;

 (3)    $H\cup L$   is the set of objects about humans or lizards.  

If we now think of   $\operatorname{tr}(.)$   as an indexing operation, then it would generate the set of attributes that deﬁnes a set of objects. Similarly,   $\mathrm{in}(.)$   is an operation that generates a set of objects that share a given set of attributes. Thus   $\operatorname{tr}(H)$  generates the attributes, or index terms, for    $H$  , and  $\operatorname{tr}(L)$   does the same thing for  $L$  . What is more interesting is to consider   $\operatorname{tr}(H\cup L)$  . Its deﬁnition is given by  

$$
\mathrm{tr}(H\cup L)=\{t\in V|a\,\Delta\,t\,\mathrm{for}\,\mathrm{all}\,a\in H\cup L\},
$$  

that is, it is the set of attributes shared by all the members of  $H$   and  $L$  . A question now arises. Is  $H\cup L$   an artiﬁcial class? For this to be the case   $\operatorname{tr}(H\cup L)$   would need to determine  $H\cup L$  , which it probably does not. For i  $\mathfrak{n}(\mathrm{tr}(H\cup L))$   the objects sharing all the attributes in  $\operatorname{tr}(H\cup L)$   is more likely to be the class of objects about vertebrates which properly includes  $H\cup L$   (and some others, e.g. ﬁsh). Thus  

$$
H\cup L\subset\operatorname{in}(\operatorname{tr}(H\cup L).
$$  

And here we have the nub of the problem. Whereas in na¨ ıve set theory one would expect equality between  $H\cup L$   and i  $\mathfrak{n}(\mathrm{tr}(H\cup L)$  , in normal use the latter set of objects in general includes    $H\cup L$  . One can salvage the situation by insisting that a class must satisfy certain conditions in order that it counts as a class, this inevitably leads to a non-Boolean logic.  

Before we extend our example any further we will deﬁne the notion of mono- thetic kinds (which philosophers call natural kinds). In terms of the example it comes down to ensuring that   $\mathbf{tr}(\mathrm{in}(.))$   and   $\mathrm{{in}(t r(.))}$   are closure operations. Let us begin by deﬁning the mathematical nature of tr and in. They are a Galois connection (see Hardegree, 1982, Davey and Priestley, 1990 and Ganter and Wille, 1999).  

# Deﬁnition D5  

Let   $(P,\leq{}_{1})$   and   $(Q,\leq{}_{2})$   be two partially ordered sets. Then a Galois connection between these two posets is, by deﬁnition, a pair of functions   $(f,\,g)$   satisfying the following conditions:  

(1)  $f{\mathrm{~mapp~}}P$   into    $Q;g$   maps  $Q$   into  $P$  ;

 (2) for all    $a,b$   in  $P$  , if  $a\leq_{1}b$   then  $f\!(a)\geq_{2}f\!(b)$  ;

 (3) for all  $x,y$   in    $Q$  , if  $x\leq_{2}y$   then    $g(x)\geq_{1}g(y)$  ;

 (4) for all    $a\in P$  ,  $a\leq_{1}g[f(a)]$  ;

 (5) for all    $x\in Q,x\leq_{2}f[g(x)]$  .  

One can easily show that (tr, in) as deﬁned in D3 and D4 is a Galois connection between    $\wp(\Omega)$   and  $\wp(V)$  , the power sets of    $\Omega$   and    $V$  respectively.  

We can now deﬁne a closure operation on a Galois connection. For this we need the deﬁnition of a  closure  operation  $c$   on a poset, say   $(R,\leq)$  , where for all  $a,b\in R$   we have  

(1)    $a\leq c(a)$  ;

 (2) if    $a\leq b$   then    $c(a)\leq c(b)$  ;

 (3)  c  $c[c(a)]=c(a)$  );  

Now let us look at the operations on the structure deﬁned by    $\Omega$  ,    $V$   and the relation    $\Delta$   which are used to deﬁne tr and in. We say that a subset of    $A$   of    $\Omega$   is Galois closed  if and only if   $\operatorname{in}[\operatorname{tr}(A)]=A$  ; a subset of    $T$   of    $V$   is  Galois closed  if and only if   $\operatorname{tr}[\operatorname{in}(T)]=T.$  . This is not automatic, for the earlier example where  $H\cup L\subset\operatorname{in}(\operatorname{tr}(H\cup L)$   showed that  $H\cup L$   is  not  Galois closed. So, with this new machinery we can now say that the Galois closed subsets of    $\Omega$   are the artiﬁcial classes. We can now go on to deﬁne the monothetic kinds.  

# Deﬁnition D6  

Let    $\Omega$  ,    $V$   and    $\Delta$   be as deﬁned before and let (tr, in) be the associated Galois connection. A  monothetic  kind is deﬁned as an ordered pair   $(A,I)$   satisfying  

1. $A\subseteq\Omega$ ;

2. $I\subseteq V$ ;

3. $\operatorname{tr}(A)=T$ ;

4. i  ${\mathfrak{n}}(T)=A$  ;  

In other words,    $T$   determines  $A$   and    $A$   determines    $T.$  . This is a very strong requirement. For example, most classiﬁcation algorithms do not produce such classes but instead produce  polythetic  kinds (see Van Rijsbergen, 1979a). The nearest thing to an algorithm producing monothetic kinds is the   $\mathrm{L}^{*}$  algorithm described in (Van Rijsbergen, 1970, Sibson, 1972).  

Hardegree (1982) in his paper goes on to develop a logic based on these kinds, and we will return to this when we discuss logics on a more abstract space, a Hilbert space.  

Let us now return to the example about humans and lizards and let us see how a non-standard logic arises. Let  $H,L$   and  $B$   be three kinds (possibly human, lizard and bird), and assuming that we have a logic for kinds, conjunction and disjunction are given by  

$$
\begin{array}{r}{K_{1}\wedge K_{2}=(A_{1}\cap A_{2},\operatorname{tr}(A{1}\cap A2)),}\\ {K_{1}\vee K_{2}=(\operatorname{in}(T_{1}\cap T_{2}),T_{1}\cap T_{2}),}\end{array}
$$  

where    $K_{1}=(A_{1},\,T_{1})$   and    $K_{2}=(A_{2},\,T_{2})$   are monothetic kinds. The sets of monothetic kinds make up a complete lattice where conjunction (join) and disjunction(meet)are de ned in the usual way.Returning to the simple example, consider  $B\wedge(H\vee L)$   and   $(B\wedge H)\vee(B\wedge L)$  : if the distributive law were to hold then these expressions would be equal, but  $H\vee L$   is by deﬁnition (lattice theory) the smallest kind that includes both  $H$   and  $L$  , which is probably the vertebrate kind, call it    $U.$  . And so  $B\wedge(H\vee L)=B\wedge U;$  ; if  $B$   is thought of as the bird kind then    $B\wedge U=B$  . But now consider the other expression,   $(B\wedge H)\vee(B\wedge L)$  . It is straightforward to argue that    $B\wedge H\!=\!B\wedge L\!=$  empty (the null kind), hence

  $(B\wedge H)\vee(B\wedge L)$   is empty,  and the distributive law fails . In classical logic

 (Boolean logic) the distributive law holds, and so Boolean logic cannot be an appropriate logic for monothetic kinds. Or to put it differently: Boolean logic is classless.  

The obvious question to ask is, does this matter? Well, it does, especially if one is interested in deﬁning classes in an abstract space, such as a vector space. Here is a geometric demonstration.  

![](images/3a2a519ddcfc6b1325e1dbff49863082ecf290ba5ecacb8491292ee11914d57f.jpg)  

In this 2-dimensional space 10   the class of documents about humans is given by the subspace  $H$  , the class about birds by    $B$  , and the class about lizards by    $L$  . (This is a very crude example.) Now deﬁne    $H\vee L$   by the subspace spanned by  $H$   and  $L$  ,  $H\wedge L$   as the intersection of the subspace corresponding to    $H$   and the subspace corresponding to  $L$  . Similarly for the join and meet of the other classes. The subspace corresponding to  $H\vee L$   will be the entire 2-dimensional plane, and thus    $B\wedge(H\vee L)=B$  , whereas geometrically   $(B\wedge H)\vee(B\wedge L)$  will again be empty, the null space. Once again the distribution law fails. If one intends to introduce logical reasoning within a vector space then this issue has to be confronted.  

The problem also has to be avoided when the Galois connection is interpreted as an inverted ﬁle relation. Intersection of the posting lists (buckets) of index terms works without any problems, so does the union of lists, and indeed this is how Boolean retrieval is implemented. But the operations intersection and union do not necessarily correspond to the equivalent logical notions for artiﬁcial classes. They are simple convenient ways of talking logically about set-theoretic operations relying on the Stone Representation Theorem. This is convenient and comfortable in the context of retrieving textual objects,but consider now the case of retrieving from a set of image objects where retrieval is based on the contents (a largely unsolved problem). The attributes, more accurately thought of as features, are not conveniently available as index terms (no visual keywords!). In general the attributes are generated through quite complex and sophisticated processing, and the assumption that the conjunction (or disjunction) of two attributes is representable by the intersection (or union) of lists of objects does not seem as intuitive as it is for text. Much more likely is that the language of features to describe image objects will have a logic which will be different from a Boolean logic. Earlier on we saw an example, showing how incompatibility of features and user-dependent assessment of features led to a non-classical logic. Similar arguments apply when interacting with images, even more strongly.  

Finally, there is a very interesting structural issue that has to do with dualit y . The deﬁnition of an artiﬁcial class is given in terms of necessary and sufﬁcient conditions by deﬁnition D1. A consequence of this is that one could equally well talk about artiﬁcial classes in the attributes which correspond to the object classes. Without going into the details, it can be understood that the logic for object classes is reﬂected as a logic in the attribute classes and also vice versa. This symmetry is often referred to as  duality , a notion that will recur. Later on we will illustrate how subspaces in an abstract space correspond to projectors into the space, more precisely the set of projectors are in 1:1 correspondence with the subspaces of the abstract space. This is important and signiﬁcant because in many ways the logic associated with the attribute space is more natural to deal with than the one on the object space. In IR terms, a logic capturing the relations between index terms is more intuitive than one concerned with subsets of documents. But more about this later.  

# Further reading  

This chapter uses only elementary concepts from set theory and logic, and summary details for these concepts can be found in Marciszewski (1981). The elements of lattice theory and order on classes are readily accessible in the classic textbook by Birkhoff and MacLane (1957). Holland (1970) contains material on lattices with an eye to its application in Hilbert space theory and hence ready for use in quantum theory. For more background on non-classical logic and, in particular, conditionals, Priest (2001) is recommended. The book by Barwise and Seligman (1997), especially Chapter 2, makes good comple- mentary reading as it also draws on the work of Hardegree (1982).  

# 3 Vector and Hilbert spaces  

The purpose of this chapter is to lay the foundations for a logic on a vector space, or a Hilbert space (see Appendix I), and for a speciﬁcation of an algebraic realisation. We will begin by introducing the basics of vector spaces, which of course may be found in many textbooks.   We will introduce elementary ﬁnite- dimensional vectors through their realisation as  $n$  -dimensional vectors in a  real Euclidean space (Halmos, 1958, p. 121). For most practical purposes this will be sufﬁcient, and has the great attraction of being quite rigorous and also very intuitive. When we move to more general spaces the extension will be noted; for example, sometimes we will allow the scalars to be complex.  

The set of all    $n$  -dimensional vectors  $\underline{{\mathbf{X}}}.$  , displayed as follows,  

$$
{\underline{{\tt x}}}={\begin{array}{l}{{\binom{x_{1}}{\cdot}}}\\ {\cdot}\\ {\cdot}\\ {\cdot}\\ {x_{n}}\end{array}}=|{\underline{{\tt x}}}\rangle,
$$  

make up the vector space. Here we have a number of notations that need clari- fying. Firstly, we can simply refer to a vector by x, or by a particular realisation using what is called a  column vector , or through the Dirac notation    $\left|\underline{{\mathbf{X}}}\right\rangle$  which is known as a  ket .   It is now easy to represent addition and multiplication.  

$$
\mathtt{\underline{{x}}}=\left(\begin{array}{c}{x_{1}}\\ {\cdot}\\ {\cdot}\\ {\cdot}\\ {x_{n}}\end{array}\right)\quad\mathrm{and}\quad\mathtt{\underline{{y}}}=\left(\begin{array}{c}{y_{1}}\\ {\cdot}\\ {\cdot}\\ {\cdot}\\ {y_{n}}\end{array}\right)
$$  

then  

$$
\underline{{\mathtt{x}}}+\underline{{\mathtt{y}}}=|\underline{{\mathtt{x}}}\rangle+|\underline{{\mathtt{y}}}\rangle=\left(\begin{array}{c}{x_{1}+y_{1}}\\ {\cdot}\\ {\cdot}\\ {\cdot}\\ {x_{n}+y_{n}}\end{array}\right),
$$  

addition is done component by component, or as is commonly said, component- wise. Multiplication by a scalar    $\alpha$   is  

$$
\alpha_{\underline{{{\mathbb{X}}}}}=\alpha|_{\underline{{{\mathbb{X}}}}}\rangle=\left(\begin{array}{c}{\alpha x_{1}}\\ {.}\\ {.}\\ {.}\\ {\alpha x_{n}}\end{array}\right)
$$  

A linear combination of a set of vectors    $\left\{\underline{{\mathbf{x}}}_{1},\dots,\underline{{\mathbf{x}}}_{n}\right\}$   is deﬁned as  

$$
{\underline{{\mathbf{y}}}}=c_{1}{\underline{{\mathbf{x}}}}_{1}+\cdot\cdot\cdot+c_{n}{\underline{{\mathbf{x}}}}_{n},
$$  

where y is another vector generated in the vector space.  

These vectors    $\left\{\underline{{\mathbf{x}}}_{1},\,.\,.\,.\,.\,,\,\underline{{\mathbf{x}}}_{n}\right\}$   are  linearly dependent  if there exist constant scalars    $c_{1},.\,.\,.\,,c_{n}$  , not all zero, such that  

$$
c_{1}\underline{{\mathbf{x}}}_{1}+\cdot\cdot\cdot+c_{n}\underline{{\mathbf{x}}}_{n}=\underline{{{0}}},
$$  

that is, they generate the  zero vector , which we will normally write as 0 without the underscore. Intuitively this means that if they are dependent, then any vector can be expressed as a linear combination of some of the others. Thus vectors  $\left\{{\underline{{\mathbf{x}}}}_{1},.\,.\,.\,.\,,{\underline{{\mathbf{x}}}}_{n}\right\}$   are  linearly independent  if    $c_{1}\underline{{\mathbf{x}}}_{1}+\cdot\cdot\cdot+c_{n}\underline{{\mathbf{x}}}_{n}=\underline{{{0}}}.$  , if and only if  $c_{1}=c_{2}=\cdot\cdot\cdot=c_{n}=0$  .  

A set of    $n$   linearly independent vectors in an  $n$  -dimensional vector space    $V_{n}$  form a  basis  for the space. This means that every arbitrary vector   ${\underline{{\mathbf{X}}}}\in V_{n}$   can be expressed as a unique linear combination of the basis vectors,  

$$
{\underline{{\mathbf{x}}}}=c_{1}{\underline{{\mathbf{x}}}}_{1}+\cdot\cdot\cdot+c_{n}{\underline{{\mathbf{x}}}}_{n},
$$  

2  The Dirac notation is explained in Dirac (1958) and related to modern algebraic notation in Sadun (2001), there is also a brief summary and explanation in Appendix I.  

where the    $c_{i}$   are called the co-ordinates of   $\underline{{\mathbf{X}}}$   with respect to the basis set

  $\left\{{\underline{{\mathbf{x}}}}1,\cdot\cdot\cdot,{\underline{{\mathbf{x}}}}n\right\}$  . To emphasise the origin of the co-ordinates x is usually written as

  ${\underline{{\mathbf{x}}}}=x_{1}{\underline{{\mathbf{x}}}}_{1}+\cdot\cdot\cdot+x_{n}{\underline{{\mathbf{x}}}}_{n}$  . There is a set of standard basis vectors which are con- ventionally used unless an author speciﬁes the contrary, these are  

$$
\underline{{\boldsymbol{\mathrm{e}}}}_{1}={\left(\begin{array}{l}{1}\\ {0}\\ {\cdot}\\ {\cdot}\\ {0}\end{array}\right)}\,,\underline{{\boldsymbol{\mathrm{e}}}}_{2}={\left(\begin{array}{l}{0}\\ {1}\\ {\cdot}\\ {\cdot}\\ {0}\end{array}\right)}\,,\dots,\underline{{\boldsymbol{\mathrm{e}}}}_{n}={\left(\begin{array}{l}{0}\\ {0}\\ {\cdot}\\ {\cdot}\\ {1}\end{array}\right)}\,.
$$  

The  $\underline{{\mathbf{e}}}_{i}$   are linearly independent, and  $\underline{{\mathbf{X}}}$   is written conventionally as  

$$
{\underline{{\boldsymbol{\mathrm{x}}}}}=x_{1}{\underline{{\boldsymbol{\mathsf{e}}}}}_{1}+\cdot\cdot\cdot+x_{n}{\underline{{\boldsymbol{\mathsf{e}}}}}_{n}={\left(\begin{array}{l}{x_{1}}\\ {x_{2}}\\ {\phantom{x_{1}}\cdot\cdot}\\ {\phantom{x_{1}}\cdot}\\ {x_{n-1}}\\ {x_{n}}\end{array}\right)}\,.
$$  

Notice that the zero vector using this new notation comes out as a vector of all zeroes:  

$$
{\underline{{\boldsymbol{\mathrm{x}}}}}=0{\underline{{\boldsymbol{\mathrm{e}}}}}_{1}+\cdot\cdot\cdot+0{\underline{{\boldsymbol{\mathrm{e}}}}}_{n}={\begin{array}{l}{0}\\ {0}\\ {\cdot\cdot}\\ {\cdot\cdot}\\ {0}\\ {0}\end{array}}.
$$  

The  transpose  of a vector  $\underline{{\mathbf{X}}}$   is  ${\underline{{\mathbf{x}}}}^{\mathrm{T}}=(x_{1},.\,.\,.\,,x_{n})$  , which is called a  row vector . In the Dirac notation this denoted by    $\big<\underline{{\mathbf{X}}}\big|$  , the so-called  bra .  

Let us now deﬁne an  inner product  (dot product) on a vector space    $V_{n}$   where the scalars are real.   The inner product is a real-valued function on the cross product    $V_{n}\ \times\ V_{n}$   ass ing with each pair of vectors   $(\underline{{\boldsymbol{\mathbf{x}}}},\,\underline{{\boldsymbol{\mathbf{y}}}})$   a unique real number. The function (. , .) has the following properties:  

I(1)  $(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})=(\underline{{\mathbf{y}}},\underline{{\mathbf{x}}}),$  , symmetry; I(2)  $(\underline{{\mathbf{x}}},\lambda\underline{{\mathbf{y}}})=\lambda(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})$  ; I(3)  $(\underline{{\mathrm{x}}}_{1}+\overline{{\mathrm{x}}}_{2},\underline{{\mathrm{y}}})=\overline{{(\underline{{\mathrm{x}}}}}_{1},\underline{{\mathrm{y}}})+(\underline{{\mathrm{x}}}_{2},\underline{{\mathrm{y}}});$  I(4)  $\left(\underline{{\mathbf{x}}},\underline{{\mathbf{x}}}\right)\geq0$  ,  and   $\left({\underline{{\mathbf{x}}}},{\underline{{\mathbf{x}}}}\right)=0$   when  $\underline{{\mathbf{x}}}=\underline{{\boldsymbol{0}}}$  .  

3  This deﬁnition could have been relegated to Appendix I, but its occurrence is so ubiquitous in both IR and QM that it is reproduced here.  

Some obvious properties follow from these, for example,  

$$
(\underline{{\boldsymbol{\mathrm{x}}}},\alpha_{1}\underline{{\boldsymbol{\mathrm{y}}}}_{1}+\alpha_{2}\underline{{\boldsymbol{\mathrm{y}}}}_{2})=\alpha_{1}(\underline{{\boldsymbol{\mathrm{x}}}},\underline{{\boldsymbol{\mathrm{y}}}}_{1})+\alpha_{2}(\underline{{\boldsymbol{\mathrm{x}}}},\underline{{\boldsymbol{\mathrm{y}}}}_{2})
$$  

thus the inner product is linear in the second component, and because of sym- metry it is also linear in the ﬁrst component.  

There will be times when the vector space under consideration will have as its ﬁeld of scalars the complex numbers. In that case the  $n$  -dimensional vectors are columns of complex numbers:  

$$
\underline{{\boldsymbol{\mathrm{x}}}}=\left(\begin{array}{c}{z_{1}}\\ {.}\\ {.}\\ {z_{n}}\end{array}\right).
$$  

In the complex case the inner product is modiﬁed slightly because the mapping  $(.\,,.)$   now maps into the set of complex numbers; Halmos (1958) in Section 60 gives an interesting discussion about complex inner products. All the properties above hold except for I(1), which now reads  

and of course affects some of the consequences. Whereas a real inner product was linear in both its components, a complex inner product is only linear in the second component and  conjugate  linear in the ﬁrst. This is easy to show,  

$$
\begin{array}{r}{(\alpha_{1}\underline{{\mathtt{x}}}_{1}+\alpha_{2}\underline{{\mathtt{x}}}_{2},\underline{{\mathtt{y}}})=\overline{{(\underline{{\mathtt{y}}},\alpha_{1}\underline{{\mathtt{x}}}_{1}+\alpha_{2}\underline{{\mathtt{x}}}_{2})}}}\\ {=\overline{{\alpha_{1}(\underline{{\mathtt{y}}},\underline{{\mathtt{x}}}_{1})}}+\overline{{\alpha_{2}(\underline{{\mathtt{y}}},\underline{{\mathtt{x}}}_{2})}}}\\ {=\overline{{\alpha_{1}}}(\underline{{\mathtt{x}}}_{1},\underline{{\mathtt{y}}})+\overline{{\alpha_{2}}}(\underline{{\mathtt{x}}}_{2},\underline{{\mathtt{y}}}),}\end{array}
$$  

where  $\alpha_{1},\,\alpha_{2}$  complex numbers to derive the transformation. Should    $\alpha_{1},\alpha_{2}$   be real, then the expression reverts to one for a real inner product.  

A standard inner product (there are many, see e.g. Deutsch, 2001) is given by  

$$
\begin{array}{r l}&{(\underline{{\mathrm{x}}},\underline{{\mathrm{y}}})=\displaystyle\sum_{i=1}^{n}\overline{{x}}_{i}y_{i}}\\ &{\qquad=\displaystyle\sum_{i=1}^{n}x_{i}y_{i}\mathrm{\;when\;the\;vector\;space\;is\;real.}}\end{array}
$$  

Using the column and row vector notation, this inner product is representable as  

$$
(\overline{{\mathbf{x}}}_{1},\hdots,\overline{{\mathbf{x}}}_{n})\left(\begin{array}{c}{y_{1}}\\ {\cdot}\\ {\cdot}\\ {\cdot}\\ {y_{n}}\end{array}\right)\quad\mathrm{and}\quad(x_{1},\hdots,x_{n})\left(\begin{array}{c}{y_{1}}\\ {\cdot}\\ {\cdot}\\ {\cdot}\\ {y_{n}}\end{array}\right),
$$  

the sum is obtained by matrix multiplication, doing a component-wise mul- tiplication of a row by a column. A more condensed notation is achieved by setting  

$$
\begin{array}{r l}&{\underline{{\boldsymbol{\mathrm{x}}}}^{\mathrm{T}}=(x_{1},\ldots,x_{n}),\;\mathrm{the~transposed},}\\ &{\underline{{\boldsymbol{\mathrm{x}}}}^{*}=(\overline{{x_{1}}},\ldots,\overline{{x_{n}}}),\;\mathrm{the~adjoint}.}\end{array}
$$  

We can thus write the inner product   $(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})$   as  $\underline{{\boldsymbol{\mathrm{X}}}}^{\mathrm{T}}\underline{{\boldsymbol{\mathrm{y}}}}$   or  $\mathrm{\underline{{x}}^{*}y}$  , a row matrix times a column matrix; and in the Dirac notation we have    $\langle\underline{{\mathbf{x}}}\mid\underline{{\mathbf{y}}}\rangle$  .  

We now return to considering real vector spaces until further notice, and proceed to deﬁning a  norm  induced by an inner product. Its geometric interpre- tation is that it is the length of a vector. It is a function    $\lVert.\rVert$  from    $V_{n}$   to the reals. One such norm is  

$$
\|{\underline{{\mathbf{x}}}}\|={\sqrt{\left({\underline{{\mathbf{x}}}},{\underline{{\mathbf{x}}}}\right)}},
$$  

which by property I(4) is always a real number. When we have the standard inner product, we get  

$$
\|{\underline{{\mathbf{x}}}}\|={\sqrt{\sum_{i=1}^{n}x_{i}^{2}}}=\left(x_{1}^{2}+\cdot\cdot\cdot+x_{n}^{2}\right)^{1/2}.
$$  

With this norm we can go on to deﬁne a distance between two vectors  $\underline{{\mathbf{X}}}$  and   $\underline{{\boldsymbol{\mathrm{y}}}}.$  ,  

$$
d({\underline{{\mathbf{x}}}},{\underline{{\mathbf{y}}}})=\|{\underline{{\mathbf{x}}}}-{\underline{{\mathbf{y}}}}\|={\sqrt{({\underline{{\mathbf{x}}}}-{\underline{{\mathbf{y}}}},{\underline{{\mathbf{x}}}}-{\underline{{\mathbf{y}}}})}}=((x_{1}-y_{1})^{2}+\cdot\cdot\cdot+(x_{n}-y_{n})^{2})^{1/2}.
$$  

A vector  ${\underline{{\mathbf{X}}}}\in V_{n}$   is a  unit vector , or  normalised , when    $\|{\underline{{\mathbf{x}}}}\|=1$  , that is when it has length one. The basic properties of a norm are  

N(1)  $\left\|{\underline{{\mathbf{X}}}}\right\|\geq0$   and    $\|{\underline{{\mathbf{x}}}}\|=0$   if and only if   $\underline{{\mathbf{X}}}=0$  ; N(2)  $\|\alpha_{\underline{{\mathbf{X}}}}\|=|\alpha|\|\underline{{\mathbf{x}}}\|$  for all    $\alpha$   and x; N(3)  $\forall_{\underline{{\mathbf{X}}}},\underline{{\mathbf{y}}},\,|(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})|\,\leq\,\|\underline{{\mathbf{x}}}\|\,\|\underline{{\mathbf{y}}}\|.$  .  

5  Hence the bra(c)ket name for it. It is also sometimes denoted as    $\langle\underline{{\mathbf{x}}}\parallel\underline{{\mathbf{y}}}\rangle$  .  

Property N(3) is known as the Cauchy–Schwartz inequality and is proved in most introductions to linear algebra (e.g. Isham, 1989). One immediate conse- quence of property   $\mathbf{N}(3)$   is that we can write  

$$
(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})=\|\underline{{\mathbf{x}}}\|\,\|\underline{{\mathbf{y}}}\|\cos\varphi,\qquad0\leq\varphi\leq\pi,
$$  

where  $\varphi$   is the angle between the two vectors  $\underline{{\mathbf{X}}}$   and y. We can now formally write down the cosine coefﬁcient (correlation) that is so commonly used in IR to measure the similarity between two documents vectors,  

$$
\cos\varphi={\frac{({\underline{{\mathbf{x}}}},{\underline{{\mathbf{y}}}})}{\|{\underline{{\mathbf{x}}}}\|\,\|{\underline{{\mathbf{y}}}}\|}}={\frac{\displaystyle\sum_{i=1}^{n}x_{i}y_{i}}{\displaystyle{\sqrt{\sum x_{i}^{2}}}\times{\sqrt{\sum x_{i}^{2}}}}}.
$$  

If the vectors   $\underline{{\mathbf{X}}},\underline{{\mathbf{Y}}}$   are unit vectors    $\|{\underline{{\mathbf{x}}}}\|=1=\|{\underline{{\mathbf{y}}}}\|$  , that is normalised, then  

$$
\cos\varphi=\sum_{i=1}^{n}x_{i}y_{i}=({\underline{{\mathbf{x}}}},{\underline{{\mathbf{y}}}}).
$$  

Having deﬁned the distance    $d(\underline{{\mathbf{x}}},\ \underline{{\mathbf{y}}})$   between two vectors (the metric on the space), we can derive its basic properties. They are  

$$
\begin{array}{r l}&{d(\underline{{\mathtt{x}}},\underline{{\mathtt{x}}})\geq0\,\mathrm{and}\;d(\underline{{\mathtt{x}}},\underline{{\mathtt{x}}})=0\quad\mathrm{if~and~only~if\;\underline{{\mathtt{x}}}=\underline{{\mathtt{y}}}};}\\ &{d(\underline{{\mathtt{x}}},\underline{{\mathtt{y}}})=d(\underline{{\mathtt{y}}},\underline{{\mathtt{x}}})\qquad\qquad\mathrm{symmetry};}\\ &{d(\underline{{\mathtt{x}}},\underline{{\mathtt{y}}})\leq d(\underline{{\mathtt{x}}},\underline{{\mathtt{z}}})+d(\underline{{\mathtt{z}}},\underline{{\mathtt{y}}})\qquad\mathrm{triangle~inequality}.}\end{array}
$$  

An important property,  orthogonality , of a pair of vectors   $\underline{{\mathbf{x}}},\ \underline{{\mathbf{y}}}$   is deﬁned as follows:  

$$
\underline{{\mathrm{x}}}\,\mathrm{and}\,\underline{{\mathrm{y}}}\,\mathrm{are\orthonormal\if\and\only\if\(\underline{{x}},\underline{{y}})=0.}
$$  

Geometrically this means that the two vectors are perpendicular. With this property we can deﬁne an  orthonormal  basis. A set of linearly independent vectors    $\left\{{\underline{{\mathbf{x}}}}_{1},\,.\,.\,.\,,{\underline{{\mathbf{x}}}}_{n}\right\}$   constitutes an orthonormal basis for the space  $V_{n}$   if and only if  

$$
(\underline{{\mathrm{x}}}_{i},\underline{{\mathrm{x}}}_{j})=\delta_{i j}=\left(\begin{array}{c c c}{1}&{\mathrm{if}}&{i=j}\\ {0}&{\mathrm{if}}&{i\neq j}\end{array}\right).
$$  

So, for example, the standard basis    $\{{\underline{{\mathbf{e}}}}_{1},\dots,{\underline{{\mathbf{e}}}}_{n}\}$   makes up just such an orthonor- mal basis.  

An important notion is the concept of  subspace , which is a subset of a vector space that is a vector space itself. A set of vectors  spans  a vector space if every vector can be written as a linear combination of some of the vec- tors in the set. Thus we can deﬁne the subspace spanned by a set of vectors  $S=\left\{{\underline{{\mathrm{x}}}}_{1},.\ .\ .\ ,{\underline{{\mathrm{x}}}}_{m}\right\}\subset V_{n}$   as the set of linear combinations of vectors of    $S$  , that is  

$$
\operatorname{span}[S]=\{\alpha_{1}{\underline{{\mathbb{X}}}}_{1}+\cdot\cdot\cdot+\alpha_{m}{\underline{{\mathbb{X}}}}_{m}\mid{\underline{{\mathbb{X}}}}_{i}\in V_{n}\quad\mathrm{and}\quad\alpha_{i}\in\mathfrak{N}\}.^{6}
$$  

Clearly, subspaces can be related through subset inclusion, intersection and union. Inclusion is intuitive. The intersection of a set of subspaces is a subspace, but the union of a set of subspaces is not normally a subspace. Remember that we are considering ﬁnite-dimensional vector spaces here; in the inﬁnite case closure  of the subspace becomes an issue (Simmons, 1963). We will have more to say about the union of subspaces later. For the moment it is sufﬁcient to think of ‘a union operation’ as the smallest subspace containing the span of the set-theoretic union of a collection of subspaces. Interestingly, this harks back to the question of whether the union of two artiﬁcial classes makes up a class.  

In abstract terms notice what we have done. In the ﬁrst place we have deﬁned an inner product on a vector space.The inner product has induced a norm,andthe norm has induced a metric.   Norms and metrics can be deﬁned independently, that is they do not necessarily have to be induced, but in practice we tend to work with induced norms and metrics.  

One of the important applications of the theory thus far is the generation of an orthonormal basis for a space or subspace, given a set of  $p$   linearly independent vectors    $\{\underline{{\mathbf{a}}}_{i}\,|\,i=1,\,2,\,.\,.\,.\,.\,,\,p,\,p\leq n,\,\underline{{\mathbf{a}}}_{i}\,\in\,V_{n}\}$  . The task is to ﬁnd a basis of  $p$   orthonormal vectors  $\underline{{\mathsf{b}}}_{i}$   for the subspace spanned by the  $p$   vectors  $\underline{{\mathbf{a}}}_{i}$  . The method that will be described next is a well-known version of the Schmidt Orthogonal is ation Process. (Schwarz  et al ., 1973).  

# Step 1  

Choose any arbitary vector, say   $\underline{{\mathbf{a}}}_{1}$  , and normalise it to get   $\underline{{\mathsf{b}}}_{1}$  ,  

$$
\begin{array}{r l}&{r_{11}=\sqrt{(\underline{{\sf a}}_{1},\underline{{\sf a}}_{1})};}\\ &{\underline{{\sf b}}_{1}=\underline{{\sf a}}_{1}/r_{11}.}\end{array}
$$  

# Step 2  

Let   $\underline{{\mathsf{b}}}_{1},\,.\,.\,.\,,\underline{{\mathsf{b}}}_{k-1}$   be the orthonormal vectors found thus far using the linearly independent vectors  $\underline{{\mathrm{a}}}_{1},\dots,\underline{{\mathrm{a}}}_{k-1}$  , that is  

$$
(\underline{{\mathsf{b}}}_{i},\underline{{\mathsf{b}}}_{j})=\delta_{i j}\quad\mathrm{for}\quad i,\,j=1,2,\ldots,k-1.
$$  

We now construct a vector  $\underline{{\mathbf{X}}}$   with the help of  $\underline{{\mathbf{a}}}_{k}$   and the  $\underline{{\mathsf{b}}}_{1},\ldots,\underline{{\mathsf{b}}}_{k-1}$   generated so far:  

$$
\underline{{\boldsymbol{\mathrm{x}}}}=\underline{{\boldsymbol{\mathrm{a}}}}_{k}-\sum_{j=1}^{k-1}r_{j k}\underline{{\boldsymbol{\mathsf{b}}}}_{j}.
$$  

We can interpret this as constructing a vector   $\underline{{\boldsymbol{\mathbf{X}}}}$   normal to the subspace spanned by the    $\{\underline{{\mathsf{b}}}_{1},\hdots,\underline{{\mathsf{b}}}_{k-1}\}$  , or, which is the same thing, an   $\underline{{\mathbf{X}}}$  orthogonal to each  $\underline{{\mathsf{b}}}_{i}$   in turn:  

$$
(\underline{{\mathsf{b}}},\underline{{\mathsf{x}}})=(\underline{{\mathsf{b}}}_{i},\underline{{\mathsf{a}}}_{k})-\sum_{j=1}^{k-1}r_{j k}(\underline{{\mathsf{b}}}_{i},\underline{{\mathsf{b}}}_{j})=0.
$$  

This reduces to  

$$
\begin{array}{l}{(\underline{{\mathsf b}}_{i},\underline{{\mathsf a}}_{k})-r_{i k}=0,}\\ {r_{i k}=(\underline{{\mathsf b}}_{i},\underline{{\mathsf a}}_{k}).}\end{array}
$$  

Since the  $\underline{{\mathsf{b}}}_{i}$   are normalised, these  $r_{i k}$   are the projections of   $\underline{{\mathbf{a}}}_{k}$   onto each   $\underline{{\mathsf{b}}}_{i}$   in turn. The new basis vector  $\underline{{\mathsf{b}}}_{k}$   is now given by  

$$
\begin{array}{r l}&{\underline{{\mathsf{b}}}_{k}=\frac{\left(\underline{{\mathsf{a}}}_{k}-\displaystyle\sum_{j=1}^{k-1}r_{j k}\,\underline{{\mathsf{b}}}_{j}\right)}{r_{k k}},}\\ &{\mathrm{e}\,r_{k k}=\left(\underline{{\mathsf{a}}}_{k}-\displaystyle\sum_{j=1}^{k-1}r_{j k}\,\underline{{\mathsf{b}}}_{j},\underline{{\mathsf{a}}}_{k}\sum_{j=1}^{k-1}r_{j k}\,\underline{{\mathsf{b}}}_{j}\right)^{1/2},}\\ &{\vdots}\end{array}
$$  

$$
\underline{{\mathsf{b}}}_{k}:(\underline{{\mathsf{b}}}_{k},\underline{{\mathsf{b}}}_{k})=1
$$  

One of the beauties of this normalisation process is that we can dynamically grow the basis incrementally without having to re-compute the basis constructed sofar.Tocompute  $[\underline{{\mathsf{b}}}_{1},\ldots,\underline{{\mathsf{b}}}_{k}]$  wecompute  $\underline{{\mathsf{b}}}_{k}$   and simply add it to  $\{\underline{{\mathsf{b}}}_{1},\hdots,\underline{{\mathsf{b}}}_{k-1}\}$  forming the new basis for the enlarged subspace. Of course a prior requirement is that the  $\underline{{\mathbf{a}_{i}}}$   are linearly independent. An obvious application of this process is the construction of a  user-speciﬁed  subspace based on document vectors identiﬁed incrementally by a user during a browsing process.  

We are now ready for an introduction to operators that act on a vector or Hilbert space, the topic of the next chapter.  

# Further reading  

For an immediate example of how the vector space representation is used in document retrieval see Salton and McGill (1983) and Belew (2000); both these textbooks give nice concrete examples. Appendix I gives a brief deﬁnition of Hilbert space. One of the most elementary introductions to vector, or Hilbert, spaces may be found in Hughes (1989). Cohen (1989) gives a precise and short introduction to Hilbert space as a lead in to the presentation of quantum logics. Another good introduction to Hilbert spaces is given by Lomonaco (2002), Chapter I, in the context of Quantum Computation. This latter introduction is beautifully presented. More references can be found in Appendix I.  

# 4  

# Linear transformations, operators and matrices  

We now introduce the idea of a linear transformation (or operator) from one vector space    $V_{n}$   to another    $W_{m}$  . We can see that  $W_{m}$   might be the same space as  $V_{n}$  , and it often is, but need not be so. Loosely speaking, such a transformation is a function from one space to another preserving the vector space operations. Thus, if  $\mathrm{T}$   is such an operator then 1  

$\mathrm{T}(\alpha\underline{{\mathbf{x}}})=\alpha\mathrm{T}(\underline{{\mathbf{x}}})$  ,  and  

$\mathrm{T(\underline{{x}}+\underline{{y}})=T(\underline{{x}})+T(\underline{{y}})}$  ,  or, equivalently,  $\mathrm{T}(\alpha_{\underline{{\mathbf{x}}}}+\beta\underline{{\mathbf{y}}})=\alpha\mathrm{T}(\underline{{\mathbf{x}}})+\beta\mathrm{T}(\underline{{\mathbf{y}}})$  ,  for all scalars  $\alpha$  ,  $\beta$   and vectors   $\underline{{\mathrm{x}}},\underline{{\mathrm{y}}}.$  .  

For a transformation to satisfy these requirements is for it to be linear. In general y   $(=\mathrm{T(\underline{{x}})})$   is a vector in the image space    $W_{m}$  , whereas  $\underline{{\boldsymbol{\mathrm{X}}}}$   is a vector in the domain space  $V_{n}$  . For now we are going to restrict our considerations to the case    $V_{n}=W_{m}(m=n)$  , that is, linear transformations from a vector space onto itself.  

The subject of linear transformations and operators both for ﬁnite and inﬁ- nite vector spaces is a huge subject in itself (Halmos, 1958, Finkbeiner, 1960, Riesz and Nagy, 1990, Reed and Simon, 1980). Here we will concentrate on a small part of the subject, where the transformations are represented by ﬁnite matrices. Every linear transformation on a vector space    $V_{n}$   can be represented by a square matrix, where the entries in the matrix depend on the particular basis used for the space. Right from the outset this is an important point to note: a transformation can be represented by many matrices, one corresponding to each basis, but the transformation thus represented is the same. The effect of a trans- formation on a vector is entirely determined by the effect on the individual basis vectors.  

$$
\begin{array}{r l}&{\mathrm{T}(\underline{{\mathbf{x}}})=\mathrm{T}(\alpha_{1}\underline{{\mathbf{b}}}_{1}+\cdot\cdot\cdot+\alpha_{n}\underline{{\mathbf{b}}}_{n})}\\ &{\qquad=\alpha_{1}\mathrm{T}(\underline{{\mathbf{b}}}_{1})+\cdot\cdot\cdot+\alpha_{n}\mathrm{T}(\underline{{\mathbf{b}}}_{n}).}\end{array}
$$  

Thus to know   $\mathrm{T(\underline{{x}})}$   we need to know   $\underline{{\mathbf{X}}}$   in terms of    $\{\underline{{\mathsf{b}}}_{1},\,.\,.\,.\,\,,\,\underline{{\mathsf{b}}}_{n}\}$  , that is,  $\mathtt{x}=\alpha_{1}\mathtt{b}_{1}+\cdot\cdot\cdot+\alpha_{n}\mathtt{b}_{n}$  , and the effect of   $\mathrm{T}$   on each  $\underline{{\mathsf{b}}}_{i}$  , namely  $\mathrm{T}(\underline{{\mathsf{b}}}_{i})$   for all    $i$  . The same is true for its representation in matrix form. To make the relationship between matrices and basis vectors explicit, let us assume that a transformation T is represented by a square matrix  A .  

$$
\mathbf{A}={\binom{a_{11}\quad.\quad.\quad.\quad a_{1n}}{.\quad.\quad.\quad.\quad.}}=(a_{i k}).
$$  

This matrix has  $n$   rows and    $n$   columns. If    $\{b_{1},.\,.\,.\,,b_{n}\}$   is the basis for    $V_{n}$  , then it is standard to assume that the  $k$  th column contains the co-ordinates of the transformed vector  $\mathrm{T}(\underline{{\mathsf{b}}}_{k})$  , referred to the basis    $\{b_{1},.\,.\,.\,,b_{n}\}$  .  

$$
\operatorname{T}({\underline{{\mathsf{b}}}}_{k})=\sum_{i=1}^{n}a_{i k}{\underline{{\mathsf{b}}}}_{i}.
$$  

$$
\begin{array}{r l}&{\mathbb{T}(\underline{{\mathbf{x}}})=\displaystyle\sum_{k=1}^{n}x_{k}\mathbb{T}(\underline{{\mathbf{b}}}_{k})=\displaystyle\sum_{k=1}^{n}x_{k}\sum_{i=1}^{n}a_{i k}\underline{{\mathbf{b}}}_{i}}\\ &{\quad=\displaystyle\sum_{i=1}^{n}\left(\sum_{k=1}^{n}a_{i k}x_{k}\right)\underline{{\mathbf{b}}}_{i}}\\ &{\quad=\displaystyle\sum_{i=1}^{n}y_{i}\underline{{\mathbf{b}}}_{i}=y,}\end{array}
$$  

from which we deduce that    $\begin{array}{r}{y_{i}-\sum_{k}\!a_{i k}x_{k}\!=\!0}\end{array}$   = 0,forall  $i$  ,becausethe  $\underline{{\mathbf{b}}}_{i}$   areli arly independent. In terms of the representation of both the transformation T and vectors in the space with respect to the basis  $\underline{{\mathsf{b}}}_{i}$  , we have now a computation rule for deriving y from the effect of the matrix  A  on the representation of  $\underline{{\mathbf{X}}}$  . When  

$$
\mathbf{A}=(a_{i k}),\quad\underline{{\mathbf{y}}}=\left(\begin{array}{l}{y_{1}}\\ {\,\cdot}\\ {\,\cdot}\\ {y_{n}}\end{array}\right),\,\underline{{\mathbf{x}}}=\left(\begin{array}{l}{x_{1}}\\ {\,\cdot}\\ {\,\cdot}\\ {x_{n}}\end{array}\right),
$$  

to calculate the  i th component of y we multiply the  i th row component-wise with x, thus  

$$
{\begin{array}{r}{{\binom{y_{1}}{\cdot}}}\\ {y_{i}}\\ {\cdot}\\ {y_{n}}\end{array}}={\left(\begin{array}{l l l l l}{a_{11}}&{.}&{.}&{.}&{a_{i n}}\\ {.}&{.}&{.}&{.}&{.}\\ {a_{i1}}&{.}&{a_{i k}}&{.}&{a_{i n}}\\ {.}&{.}&{.}&{.}&{.}\\ {a_{n1}}&{.}&{.}&{.}&{a_{n n}}\end{array}\right)}\,{\left(\begin{array}{l}{x_{1}}\\ {.}\\ {.}\\ {x_{n}}\end{array}\right)}\,.
$$  

(There is a sort of cancellation rule that must hold for the dimensions,  

$$
(n\times1)=(n\times n)(n\times1)=(n\times1).)
$$  

If the transformation  $\mathrm{T}$   for  $\underline{{\mathbf{y}}}=\mathrm{T}(\underline{{\mathbf{x}}})$   can be inverted, denoted   $\mathrm{T}^{-1}$  , which means that   $\underline{{\mathbf{x}}}\,=\,\mathrm{T}^{-1}(\underline{{\mathbf{y}}})$  , then it is  non-singular , otherwise it is  singular . The same is true for matrices,   $\underline{{\mathbf{x}}}=\mathbf{A}^{-1}(\underline{{\mathbf{y}}})$  , where    $\mathbf{A}^{-1}$    is the inverse matrix and exists if the corresponding transformation is non-singular; the termi- nology transfers to the representations, and so we speak of non-singular matrices.  

The arithmetic operations on matrices are largely what we would expect. Addition is simply component-wise for matrices of matching dimensions, and the same for subtraction. To multiply a matrix by a scalar, every component is multiplied by the scalar. Multiplication of matrices is exceptional as being more complex.  

The product of two transformations   $\mathrm{T}_{1}\mathrm{T}_{2}$   is deﬁned through the effect it has on a vector, so  

$$
\begin{array}{r}{\mathrm{T}_{1}\mathrm{T}_{2}(\underline{{\mathbf{x}}})=\mathrm{T}_{a}(\underline{{\mathbf{x}}}),\mathrm{~where~\mathrm{T}_{a}=\mathrm{T}_{1}\mathrm{T}_{2},}}\\ {\mathrm{T}_{2}\mathrm{T}_{1}(\underline{{\mathbf{x}}})=\mathrm{T}_{b}(\underline{{\mathbf{x}}}),\mathrm{~where~\mathrm{T}_{b}=\mathrm{T}_{2}\mathrm{T}_{1},}}\end{array}
$$  

and in general the p not commutative, that is,  $\mathrm{T}_{1}\mathrm{T}_{2}\neq\mathrm{T}_{2}\mathrm{T}_{1}$  . The same applies to matrices,  $\mathbf{A}\mathbf{B}=\mathbf{C}_{a}$   =  and    $\mathbf{BA}=\mathbf{C}_{b}$  , are calculated through their effects of    $\mathbf{B}$   followed by  $\mathbf{A}$  , or  A  followed by    $\mathbf{B}$  , on vectors,  

$$
\begin{array}{r}{\underline{{\mathrm{y}}}_{1}=\mathbf{C}_{a\underline{{\mathrm{X}}}}=\mathbf{A}\mathbf{B}\underline{{\mathrm{X}}},}\\ {\underline{{\mathrm{y}}}_{2}=\mathbf{C}_{b\underline{{\mathrm{X}}}}=\mathbf{B}\mathbf{A}\underline{{\mathrm{X}}},}\end{array}
$$  

and again, in general   $\underline{{\mathbf{y}}}_{1}\neq\underline{{\mathbf{y}}}_{2}$  . The rule for matrix multiplication is derived similarly to the rule for multiplying a matrix by a column vector (Mirsky, 1990). It is  

$$
\left(\begin{array}{c c c c}{{c_{11}}}&{{.}}&{{*}}&{{.}}&{{c_{1n}}}\\ {{.}}&{{.}}&{{.}}&{{.}}\\ {{.}}&{{.}}&{{c_{i j}}}&{{.}}&{{.}}\\ {{.}}&{{.}}&{{*}}&{{.}}&{{.}}\\ {{c_{n1}}}&{{.}}&{{*}}&{{.}}&{{c_{n n}}}\end{array}\right)=\left(\begin{array}{c c c c}{{a_{11}}}&{{.}}&{{.}}&{{.}}&{{a_{1n}}}\\ {{.}}&{{.}}&{{.}}&{{.}}\\ {{a_{i1}}}&{{*}}&{{*}}&{{a_{i n}}}\\ {{.}}&{{.}}&{{.}}&{{.}}\\ {{a_{n1}}}&{{.}}&{{.}}&{{a_{n n}}}\end{array}\right)\left(\begin{array}{c c c c}{{b_{11}}}&{{.}}&{{b_{1j}}}&{{.}}&{{b_{1n}}}\\ {{.}}&{{.}}&{{*}}&{{.}}\\ {{.}}&{{.}}&{{*}}&{{.}}\\ {{.}}&{{.}}&{{*}}&{{.}}\\ {{b_{n1}}}&{{.}}&{{b_{n j}}}&{{.}}&{{b_{n n}}}\end{array}\right).
$$  

There are several ways of expressing this product in a abbreviated form:  

$$
\begin{array}{c}{{(c_{i j})=(a_{i k})(b_{k j}),}}\\ {{c_{i j}=\displaystyle\sum_{k=1}^{n}a_{i k}b_{k j},}}\\ {{c_{i j}=a_{i k}b_{k j}.}}\end{array}
$$  

The last of the three lines uses the convention that when an index is repeated it is to be summed over. To compute the  $(i,j)$  th entry in  C  we multiply the  i th row with the  j th column component by component and add the results. It is like the Euclidean inner product between two vectors.  

# Example 1  

$$
\left({1\atop1}\quad1\right)\left({1\atop-1}\quad-1\right)=\left({1-1\atop1-1}\quad-1+1\right)=\left({0\atop0}\quad0\right).
$$  

# Example 2  

$$
\left(\!\!{\begin{array}{l l}{\cos\varphi}&{-\sin\varphi}\\ {\sin\varphi}&{-\cos\varphi}\end{array}}\!\!\right)\left({\begin{array}{l l}{1}&{0}\\ {0}&{0}\end{array}}\right)=\left(\!\!{\begin{array}{l l}{\cos\varphi}&{0}\\ {\sin\varphi}&{0}\end{array}}\!\!\right).
$$  

# Example 3  

$$
\left(\!\!{\begin{array}{c c}{1}&{0}\\ {0}&{0}\end{array}}\!\!\right)\left(\!\!{\begin{array}{c c}{\cos\varphi}&{-\sin\varphi}\\ {\sin\varphi}&{\cos\varphi}\end{array}}\!\!\right)=\left(\!\!{\begin{array}{c c}{\cos\varphi}&{-\sin\varphi}\\ {0}&{0}\end{array}}\!\!\right).
$$  

Just as there are special vectors, e.g.  $\underline{{\mathbf{e}}}_{i}$  , all zeroes except for a 1 in the  i th position, there are special matrices. In particular we have the  identity  matrix, all 1s down the diagonal and zeroes everywhere else,  

$$
\begin{array}{r}{\mathbf{I}=\left(\begin{array}{l l l l l}{1}&{0}&{0}&{0}&{0}\\ {0}&{1}&{0}&{0}&{0}\\ {0}&{0}&{1}&{0}&{0}\\ {0}&{0}&{0}&{1}&{0}\\ {0}&{0}&{0}&{0}&{1}\end{array}\right).}\end{array}
$$  

The identity matrix plays a special role, for example to deﬁne the inverse rix (if it exists), we set    $\mathbf{AB}=\mathbf{I}=\mathbf{BA}$  , from which it follows that  ${\bf B}={\bf A}^{-1}$   = , or  ${\bf A}={\bf B}^{-1}$  , or in other words that    $\mathbf{B}$   is the inverse of  A  and vice versa.  I  is the matrix that maps each vector into itself.  

Another special matrix is the zero matrix, a matrix with all zero entries, which maps every vector into the zero vector.  

It is interesting (only once!) to see what happens to a matrix of a transforma- tion when there is a change of basis. Let us say that the basis is changed from  $\{\underline{{\mathsf{b}}}_{1},\hdots,\underline{{\mathsf{b}}}_{n}\}$   to    $\{\underline{{\mathsf{b}}}_{1}^{\prime},\hdots,\underline{{\mathsf{b}}}_{n}^{\prime}\}$  , then  

$$
\begin{array}{r}{\underline{{\mathsf{b}}}_{k}^{\prime}=\underline{{\mathsf{c}}}_{\mathrm{l}k}\,\underline{{\mathsf{b}}}_{\mathrm{l}}+\cdot\cdot\cdot+\underline{{\mathsf{c}}}_{\mathrm{NL}}\,\underline{{\mathsf{b}}}_{n},\qquad k=1,\,.\,.\,,n,}\end{array}
$$  

because any vector can be expressed as a linear combination of the basis vectors. Any vector   $\underline{{\mathbf{X}}}$   referred to the new basis is  

$$
\underline{{\boldsymbol{\mathrm{x}}}}=\sum_{k=1}^{n}x_{k}^{\prime}\,\underline{{\boldsymbol{\mathrm{b}}}}_{k}^{\prime},
$$  

which when expressed with respect to the old basis  

$$
\begin{array}{l}{\displaystyle\underline{{\boldsymbol{\mathrm{x}}}}=\sum_{k=1}^{n}\boldsymbol{x}_{k}^{\prime}\sum_{i=1}^{n}c_{i k}\underline{{\boldsymbol{\mathrm{b}}}}_{i}}\\ {\displaystyle\quad=\sum_{i=1}^{n}\sum_{k=1}^{n}c_{i k}\boldsymbol{x}_{k}^{\prime}\underline{{\boldsymbol{\mathrm{b}}}}_{i}.}\end{array}
$$  

Thus  $\begin{array}{r}{x_{i}=\sum_{k=1}^{n}c_{i k}x_{k}^{\prime}}\end{array}$  , which gives us the rule for doing the co-ordinate trans- = formation corresponding to the basis change:  

$$
\begin{array}{r}{\underline{{\mathbf{x}}}=\mathbf{C}\underline{{\mathbf{x}}}^{\prime};}\end{array}
$$  

C  is a non-singular matrix, uniquely invertible.  

We can now calculate the effect of a co-ordinate transformation on a matrix. Let x, y be the co-ordinates in one basis and  $\underline{{\boldsymbol{\mathrm{x}}}}^{\prime},\underline{{\boldsymbol{\mathrm{y}}}}^{\prime}$    the co-ordinates of the same vectors in another basis. Let  A  be the matrix representing a transformation in the ﬁrst system, and  $\mathbf{B}$   represent the same transformation in the second system. Then  

$$
\begin{array}{r l}&{\underline{{\mathrm{y}}}=\mathbf{A}\underline{{\mathrm{x}}}\quad\mathrm{and}\quad\underline{{\mathrm{y}}}^{\prime}=\mathbf{B}\underline{{\mathrm{x}}}^{\prime},}\\ &{\underline{{\mathrm{x}}}=\mathbf{C}\underline{{\mathrm{x}}}^{\prime}\quad\mathrm{and}\quad\underline{{\mathrm{y}}}=\mathbf{C}\underline{{\mathrm{y}}}^{\prime},}\\ &{\underline{{\mathrm{y}}}=\mathbf{C}\underline{{\mathrm{y}}}^{\prime}=\mathbf{A}\underline{{\mathrm{x}}}=\mathbf{A}(\mathbf{C}\underline{{\mathrm{x}}}^{\prime})=\mathbf{A}\mathbf{C}\underline{{\mathrm{x}}}^{\prime}}\\ &{\Rightarrow\underline{{\mathrm{y}}}^{\prime}=\mathbf{C}^{-1}\mathbf{A}\mathbf{C}\underline{{\mathrm{x}}}}\\ &{\Rightarrow\mathbf{B}=\mathbf{C}^{-1}\mathbf{A}\mathbf{C}.}\end{array}
$$  

The two matrices    $\mathbf{A}$   and    $\mathbf{B}$   are related in this way through what is called a similarity transformation  $\mathbf{C}$  , and are said to be  similar . Many important prop- erties of matrices are invariant with respect to similarity transformations. For example, the  eigenvalues  of a matrix are invariant; more about which later.  

Another important class of special transformations (or matrices) 2   is the class of  projectors . To deﬁne them we must ﬁrst deﬁne the  adjoint  of a matrix. The deﬁning relation is  

$$
(\mathbf{A}^{*}\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})=(\underline{{\mathbf{x}}},\mathbf{A}\underline{{\mathbf{y}}}).
$$  

When the set of scalars is complex, the matrix  $\mathbf{A}^{*}$  is the complex conjugate of the transpose of  $\mathbf{A}\!:\overline{{\mathbf{A}^{\mathrm{T}}}}$  . The transpose of    $\mathbf{A}$   is simply the matrix derived by interchanging the rows with the columns.  

# Example 1 – the real case, given that  ${\mathbfit{a}},{\mathbfit{u}},{\mathbfit{x}},{\mathbfit{c}}$   are real numbers  

$$
{\binom{a\quad x}{u\quad c}}^{*}={\binom{a\quad u}{x\quad c}}\,.
$$  

# Example 2 – the complex case  

$$
{\binom{a+\mathrm{i}b\quad x-\mathrm{i}y}{u-\mathrm{i}\nu\quad c+\mathrm{i}d}}^{*}={\binom{a-\mathrm{i}b\quad u+\mathrm{i}\nu}{x+\mathrm{i}y\quad c-\mathrm{i}d}}\,.
$$  

In the real case, which we are mostly concerned with,  $\mathbf{A}^{*}=\mathbf{A}^{\mathrm{T}}$  . Operators can be  self-adjoint  (or  Hermitian ) that is,  

$$
(\mathbf{Ax},{\underline{{\mathbf{y}}}})=({\underline{{\mathbf{x}}}},\mathbf{A}{\underline{{\mathbf{y}}}}){\mathrm{~for~all~}}{\underline{{\mathbf{x}}}},{\underline{{\mathbf{y}}}}{\mathrm{~implies~that~}}\mathbf{A}=\mathbf{A}^{*}.
$$  

In a real inner product space the self-adjoint matrices are the same as the symmetric matrices. In a complex space the complex conjugate of the transpose must be equal to  A . These matrices play an important role in many applications, for example the Hermitian matrices have real eigenvalues which are exploited as the results of measurements in quantum mechanics.  

Some properties of adjoints are  

$$
\begin{array}{r}{(\mathbf{A}+\mathbf{B})^{*}=\mathbf{A}^{*}+\mathbf{B}^{*},}\\ {(\alpha\mathbf{A})^{*}=\overline{{\alpha}}\mathbf{A}^{*},\;\;\;\;\;\;\;\;}\\ {(\mathbf{A}^{*})^{*}=\mathbf{A},\;\;\;\;\;\;\;\;}\\ {\mathbf{I}^{*}=\mathbf{I},\;\;\;\;\;\;\;\;}\\ {(\mathbf{A}\mathbf{B})^{*}=\mathbf{B}^{*}\mathbf{A}^{*},\;\;\;\;\;\;\;\;}\end{array}
$$  

# Projectors  

On a vector space    $V_{n}$   the projectors 3   are idempotent, self-adjoint linear oper- ators. An operator    $\mathbf{E}$   is idempotent if    $\mathbf{E}_{\ \underline{{\mathbf{X}}}}^{2}=\mathbf{E}_{\underline{{\mathbf{X}}}}$   for all  $\underline{{\mathbf{X}}}$  , that is    $\mathbf{E}^{2}=\mathbf{E}$  , by self-adjointness we require    $\mathbf{E}=\mathbf{E}^{*}$  . Hence projection operators are both Hermitian and idempotent.  

# Example  

$$
\begin{array}{r l}{\frac{1}{2}\left(\!\!\!\begin{array}{c c}{+1}&{-\mathrm{i}}\\ {+\mathrm{i}}&{+1}\end{array}\!\!\right)\times\frac{1}{2}\left(\!\!\!\begin{array}{c c}{+1}&{-\mathrm{i}}\\ {+\mathrm{i}}&{+1}\end{array}\!\!\right)\!\!}&{=\frac{1}{4}\left(\!\!\!\begin{array}{c c}{1+1}&{-\mathrm{i}-\mathrm{i}}\\ {\mathrm{i}+\mathrm{i}}&{+1+1}\end{array}\!\!\right)}\\ &{=\frac{1}{4}\left(\!\!\!\begin{array}{c c}{+2}&{-2\mathrm{i}}\\ {+2\mathrm{i}}&{+2}\end{array}\!\!\right)=\frac{1}{2}\left(\!\!\!\begin{array}{c c}{+1}&{-\mathrm{i}}\\ {+\mathrm{i}}&{+1}\end{array}\!\!\right).}\end{array}
$$  

Projectors are operators that project onto a subspace. In fact the set of projectors on a vector space is in one-to-one correspondence with the subspaces of that space.They include the zero operator  $\mathbf{E}_{0}$   that projects every vector x to the empty subspace,  $\mathbf{E}_{0}\underline{{\mathbf{X}}}=\underline{{\underline{{0}}}}$   for all x, and the identity operator  I  which maps every vector onto itself,  $\mathbf{{\underline{{X}}}}={\underline{{\mathbf{X}}}}$   for all x. We will use projection operators extensively in the sequel, especially ones that project onto 1-dimensional spaces. For each basis vector, there is a subspace generated by it, and corresponding to it there is a projector which projects all the vectors in the space onto it. These projectors make up a collection of orthogonal projectors, because any vector orthogonal to a subspace projected onto will project to 0, and any vector already in the space will be projected to itself. Also, any vector in the space can be represented as the sum of two vectors, one a vector in a subspace and another vector in the subspace orthogonal to it.  

Let us now do an example calculation using some of these ideas. If the space is spanned by a basis    $\{\underline{{\mathsf{b}}}_{1},\,.\,.\,.\,.\,,\,\underline{{\mathsf{b}}}_{n}\}$  , and it constitutes an orthonormal set, ormalized   $\underline{{\mathbf{x}}}(\|\underline{{\mathbf{x}}}\|=1)$  ,  $\mathtt{x}=c_{1}\mathtt{b}_{1}+\cdot\cdot\cdot+c_{n}\mathtt{b}_{n}$  , we would have  ${\textstyle\sum_{i=1}^{n}|c_{i}|^{2}=1}$  
   | |  =  1 (  $c_{i}$   may be c plex 5 ). Now let  $\mathbf{P}_{i}$   be the projector corresponding = to the subspace spanned by b , then  

$$
\begin{array}{r l}&{\mathbf{P}_{i\underline{{\mathbf{X}}}}=c_{1}\mathbf{P}_{i}\underline{{\mathbf{b}}}_{1}+\cdot\cdot\cdot+c_{i}\mathbf{P}_{i}\underline{{\mathbf{b}}}_{i}+\cdot\cdot\cdot+c_{n}\mathbf{P}_{i}\underline{{\mathbf{b}}}_{n}}\\ &{\qquad=0+\cdot\cdot\cdot+c_{i}\mathbf{P}_{i}\underline{{\mathbf{b}}}_{i}+\cdot\cdot\cdot0}\\ &{\qquad=c_{i}\underline{{\mathbf{b}}}_{i}.}\end{array}
$$  

If we calculate  

$$
\begin{array}{r l}&{(\underline{{\mathbf{x}}},\mathbf{P}_{i}\underline{{\mathbf{x}}})=(\underline{{\mathbf{x}}},\mathbf{P}_{i}\mathbf{P}_{i}\underline{{\mathbf{x}}})\;\mathrm{because}\;\mathbf{P}_{i}^{*}}\\ &{\qquad\qquad=(\mathbf{P}_{i}\underline{{\mathbf{x}}},\mathbf{P}_{i}\underline{{\mathbf{x}}})=[\mathbf{P}_{i}\underline{{\mathbf{x}}}|^{2}]}\\ &{\qquad\qquad=(c_{i}\underline{{\mathbf{b}}}_{i},c_{i}\underline{{\mathbf{b}}}_{i})}\\ &{\qquad\qquad=c_{i}^{*}(\underline{{\mathbf{b}}}_{i},c_{i}\underline{{\mathbf{b}}}_{i})}\\ &{\qquad\qquad=c_{i}^{*}c_{i}(\underline{{\mathbf{b}}}_{i},\underline{{\mathbf{b}}}_{i})}\\ &{\qquad\qquad=c_{i}^{*}c_{i}\,}\\ &{\qquad\qquad=|c_{i}|^{2}\,.}\end{array}
$$  

Now remember that  ${\textstyle\sum_{i=1}^{n}|c_{i}|^{2}=1}$  =    1, hence the vector x  generated a probabil- ity distribution on the subspaces corresponding to the  $\mathbf{P}_{i}s$  s. This is an interesting result because, depending on how we choose our    $\{\underline{{\mathsf{b}}}_{1},.\.\.\,.\,,\underline{{\mathsf{b}}}_{n}\}$  , we get a dif- ferent probability distribution. This is like taking a particular point of view, a perspective from which to view the space.  

We can formalise the idea of a probability associated with a vector x more precisely, speciﬁcally, for each normalized vector  ${\underline{{\mathbf{X}}}}\in V_{n}$   deﬁne a function    $\mu_{\underline{{\mathrm{x}}}}$  on the set of subspaces of    $V_{n}$   as follows:  

$$
\mu_{\underline{{\mathbf{x}}}}(L_{i})=(\mathbf{P}_{i\underline{{\mathbf{X}}}},\mathbf{P}_{i\underline{{\mathbf{X}}}})=|\mathbf{P}_{i\underline{{\mathbf{X}}}}|^{2}.
$$  

It has the usual properties:  

(a)    $\mu_{\underline{{\mathrm{x}}}}(\underline{{0}})=0;$  ;

 (b)    $\mu_{\underline{{\mathrm{X}}}}(V_{n})=1$  ;

 (c) for subspaces  $L_{i}$   and    $L_{j},\mu_{\mathrm{x}}(L_{i}\,\oplus\,L_{j})=\mu_{\mathrm{x}}(L_{i})\,+\,\mu_{\mathrm{x}}(L_{j})$   p vided that  $L_{i}\cap L_{j}=\Phi$  , where  $L_{i}\oplus L_{j}$   the smallest subspace containing  $L_{i}$   and  $L_{j}$  .  

5    $c_{i}=a_{i}+\mathrm{i}b_{i}$  , then  $|c_{i}|^{2}=a_{i}^{2}+b_{i}^{2}$    + .  

The relationship between vectors, subspaces and probability measure will be a recurring theme, culminating in the famous theorem of Gleason (Gleason, 1957).  

# Eigenvalues and eigenvectors  

We now come to one of the more important concepts associated with linear transformations and matrices. We introduce it in terms of matrices, but of course it could equally well be discussed in terms of transformations.  

We deﬁne the  eigenvector  x of a matrix  $\mathbf{A}$   as a non-zero vector satisfying  $\mathbf{Ax}_{\underline{{\mathbf{x}}}}=\lambda_{\underline{{\mathbf{x}}}}$  , where  $\lambda$   is a scalar. The value    $\lambda$   is called an  eigenvalue  of    $\mathbf{A}^{\prime}$  associated with the eigenvector x. This apparently simple equation has a huge literature associated with it (e.g. Halmos, 1958, Wilkinson, 1965), and a detailed discussion of its theoretical signiﬁcance can be found in many a book on linear algebra (some references can be found in the bibliography).  

# Example  

$$
\mathbf{A}={\binom{0}{2}}\;{\binom{2}{0}}\;{\mathrm{and}}\;{\underline{{\mathbf{v}}}}={\binom{3}{3}}\;;
$$  

$$
\begin{array}{r}{\left(\!\!\begin{array}{c c}{0}&{2}\\ {2}&{0}\end{array}\!\!\right)\left(\!\!\begin{array}{c}{3}\\ {3}\end{array}\!\!\right)=\left(\!\!\begin{array}{c}{6}\\ {6}\end{array}\!\!\right)=2\left(\!\!\begin{array}{c}{3}\\ {3}\end{array}\!\!\right).}\end{array}
$$  

Hence  $(_{3}^{3})$  ) is an eigenvector of  $\mathbf{A}$   and 2 is an eigenvalue of  $\mathbf{A}$  .  

# Example  

$$
{\begin{array}{r l}&{{\underline{{\mathsf{u}}}}={\left(\begin{array}{l}{-3}\\ {0}\end{array}\right)}\,;}\\ &{{\left(\begin{array}{l l}{0}&{2}\\ {2}&{0}\end{array}\right)}{\binom{3}{0}}={\binom{0}{6}}\neq\lambda\,{\binom{3}{0}}{\mathrm{\,for\,any\,}}\lambda.}\end{array}}
$$  

Hence  $\underline{{\boldsymbol{\mathbf{u}}}}$   is not an eigenvector.  

# Example  

$$
{\begin{array}{r l}&{{\underline{{\boldsymbol{\mathrm{w}}}}}={\binom{-3}{3}}\,;}\\ &{{\binom{0}{2}}\,{\binom{-3}{3}}={\binom{6}{-6}}=-2\,{\binom{-3}{3}}\,.}\end{array}}
$$  

Hence w is an eigenvector and its eigenvalue is  $^{-2}$  .  

In general a matrix can have complex numbers as its entries, and the ﬁeld of scalars may also be complex. Despite this we will mostly be interested in matrices that have real  eigenvalues . For example, Hermitian matrices have eigenvalues that are all real. This means that for real matrices, symmetric matri- ces have real eigenvalues. Notice that it is possible for real matrices to have complex eigenvalues. Another important property of Hermitian and symmetric matrices is that if the eigenvalues are all distinct, that is  non-degenerate , then the eigenvectors associated with them are mutually orthogonal.  

Let  $\mathbf{Ax_{1}}=\lambda_{1}\underline{{\mathbf{x}}}$  ,    $\mathbf{A}\underline{{\mathbf{x}}}_{2}=\lambda_{2}\underline{{\mathbf{x}}}$  , and since    $\mathbf{A}$   is Hermitian,    $\lambda_{1}\neq\lambda_{2}$  ,  $\mathtt{X}_{1}\neq\mathtt{X}_{2}$  , and we have  

$$
\begin{array}{c}{\lambda_{1}(\underline{{\mathrm{x}}}_{1},\underline{{\mathrm{x}}}_{2})=(\mathbf{A}\underline{{\mathrm{x}}}_{1},\underline{{\mathrm{x}}}_{2})=(\underline{{\mathrm{x}}}_{1},\mathbf{A}\underline{{\mathrm{x}}}_{2})=\lambda_{2}(\underline{{\mathrm{x}}}_{1},\underline{{\mathrm{x}}}_{2})}\\ {0=(\lambda_{1}-\lambda_{2})(\underline{{\mathrm{x}}}_{1}-\underline{{\mathrm{x}}}_{2})}\end{array}
$$  

Hence for an    $n$  -dimensional matrix  A , for which  $\lambda_{1}\neq\lambda_{2}\neq\cdot\cdot\neq\lambda_{n}$  , we have the eigenvectors  $\underline{{\mathbf{X}}}_{i}$   satisfying  

$$
({\underline{{\mathbf{x}}}}_{i},{\underline{{\mathbf{x}}}}_{j})=\delta_{i j}={\left\{\begin{array}{l l}{1,}&{i=j,}\\ {0,}&{i\neq j.}\end{array}\right.}
$$  

We are now a position to present one of the major results of ﬁnite-dimensional vector spaces: the Spectral Theorem (Halmos, 1958). The importance of this theorem will become clearer as we proceed, but for now it may be worth saying that if an observable is seen as a question, the spectral theorem shows how such a question can be reduced to a set of yes/no questions.  

# Spectral theorem  

To any self-adjoint transformation  A  on a ﬁnite-dimensional inner product space  $V_{n}$   there correspond real numbers  $\alpha_{1},\ldots,\alpha_{r}$   and orthogonal projections  $\mathbf{E}_{1},\ldots$  ,

  $\mathbf{E}_{r},\,r\leq n$  , so that  

(1) the  $\alpha_{j}$   are pairwise distinct,

 (2) the  $\mathbf{E}_{j}$   are pairwise orthogonal   $(\perp)^{6}$    and different from 0,

 (3)  $\textstyle\sum_{j=1}^{r}\mathbf{E}_{j}=\mathbf{I}$  =  = , and

 (4)  $\begin{array}{r}{\dot{\bf A}=\sum_{j=1}^{r}\alpha_{j}{\bf E}_{j}}\end{array}$  .  

The proof of this theorem may be found in Halmos (1958). We will restrict ourselves to some comments. The    $\alpha_{i}$   are the distinct eigenvalues of    $\mathbf{A}$   and  

6  A symbol commonly used to indicate orthogonality,  $\mathbf{E}_{i}\perp\mathbf{E}_{j}$  , if and only if    $\mathbf{E}_{i}\mathbf{E}_{j}=\mathbf{E}_{j}\mathbf{E}_{i}=0$  .  

the projectors    $\mathbf{E}_{i}$   are those corresponding to the subspaces generated by the eigenvectors. If there are    $n$   distinct eigenvalues each of these subspaces is 1-dimensional, but if not then some of the eigenvalues are  degenerate , and the subspace corresponding to such a degenerate eigenvalue will be of higher dimensionality than 1. Also notice that we have only needed an inner product on the space, there was no need to call on its induced norm or metric. Many calculations with Hermitian matrices are simpliﬁed because to calculate their effects we only need to consider the effects of the set of projectors    $\mathbf{E}_{i}$  .  

Look how easy it is to prove that each  $\alpha_{i}$   is an eigenvalue of  A . By (2)

  $\mathbf{E}_{i}\perp\mathbf{E}_{j}$  , now  a vect  $\underline{{\boldsymbol{\mathbf{X}}}}$  n the subspace onto which  $\mathbf{E}_{j}$   projects, then

  $\mathbf{E}_{j\underline{{\mathbf{X}}}}=\underline{{\mathbf{X}}}$  , and  $\mathbf{E}_{i}\underline{{\mathbf{x}}}=0$   =  0 for all  i  $i\neq j$   ̸= , thus  

$$
\mathbf{A}_{\underline{{\mathbf{X}}}}=\sum_{i}\alpha_{i}\mathbf{E}_{i\underline{{\mathbf{X}}}}=\alpha_{j}\mathbf{E}_{j\underline{{\mathbf{X}}}}=\alpha_{j\underline{{\mathbf{X}}}}.
$$  

Hence  $\alpha_{j}$   is an eigenvalue.  

In the Dirac notation 7   these projectors take on a highly informative, but condensed, form. Let  $\varphi_{i}$   be an eigenvector and    $\alpha_{i}$   the corresponding eigenvalues of    $\mathbf{A}$  , then    $\mathbf{E}_{i}$   is denoted by  

$$
\begin{array}{c}{{{\bf E}_{i}=|\varphi_{i}\rangle\langle\varphi_{i}|,\,\mathrm{or}}}\\ {{=|\alpha_{i}\rangle\langle\alpha_{i}|,}}\end{array}
$$  

where the    $\varphi_{i}$   and  $\alpha_{i}$   are used as labels.  

Remember that    $|.\rangle$  indicates a column vector and    $\langle.|$   a row vector. This notation is used to enumerate the    $\mathbf{E}_{i}$   explicitly in terms of the projectors cor- responding to the orthonormal basis given by the eigenvectors of    $\mathbf{A}$  . Its power comes from the way it facilitates calculation, for example,  

$$
\mathbf{E}_{i\underline{{\mathbf{X}}}}=\left|\varphi_{i}\right\rangle\left\langle\varphi_{i}\right|\underline{{\mathbf{X}}}\rangle,
$$  

but    $\langle\varphi_{i}|\underline{{\mathbf{x}}}\rangle$  is the projection of  $\underline{{\boldsymbol{\mathbf{X}}}}$   onto the unit vector    $\varphi_{i}$  , so  

$$
\mathbf{E}_{i}=x_{i}|\varphi_{i}\rangle,{\mathrm{~where~}}x_{i}=\langle\varphi_{i}|_{\underline{{\mathbf{X}}}}\rangle,
$$  

The spectral representation, or spectral form, of    $\mathbf{A}$   is written as  

$$
\mathbf{A}=\sum_{i=1}^{n}\alpha_{i}|\varphi_{i}\rangle\,\langle\varphi_{i}|
$$  

if  $\mathbf{A}$   has  $n$   non-degenerate eigenvalues.  

7  Consult Appendix I for a brief introduction to the Dirac notation.  

Becoming familiar with the Dirac notation is well worth while. It is used extensively in the classical books on quantum mechanics, but rarely explained in any detail. The best sources for such an explanation are Dirac (1958), the master himself, Sadun (2001), which makes the connection with normal linear algebra, and Grifﬁths (2002), which introduces the notation via its use in quantum mechanics. There is also a crash course in Appendix I.  

This completes the background mathematics on vector spaces and operators that will take us through the following chapters.  

# Further reading  

In addition to the standard texts referenced in this chapter, the books by Fano (1971) and Jordan (1969) are good introductions to linear operators in Hilbert space. A very clear and simple introduction can be found in Isham (1989) and Schmeidler (1965). Sometimes the numerical and computational aspects of linear algebra become important, for that the reader is advised to consult Wilkinson (1965), Golub and Van Loan (1996), Horn and Johnson (1999) and Collatz (1966). The most important result in this chapter is the Spectral Theo- rem, for further study Arveson (2000), Halmos (1951) and Retherford (1993) are recommended. Recent books on advanced linear algebra and matrix theory are, respectively, Roman (1992) and Zhang (1999).  

# 5 Conditional logic in IR  

We have established that the subspaces in a Hilbert Space are in 1:1 corre- spondence with the projectors onto that space, that is, to each subspace there corresponds a projection and vice versa. In the previous chapters we have shown how subsets and artiﬁcial classes give us a semantics for rudimentary retrieval languages. What we propose to do next is to investigate a seman- tics based on subspaces in a Hilbert space and see what kind of retrieval lan- guage corresponds to it. In particular we will be interested in the nature of conditionals.  

To appreciate the role and value of conditionals in IR we look a little more closely at how they arise in the application of logic to IR. When retrieval is modelled as a form of inference it becomes necessary to be explicit about the nature of conditionals. It is simplest to illustrate this in terms of textual objects. A document is seen as a set of assertions or propositions and a query is seen as a single assertion or proposition. Then, a document is considered relevant to a query if it implies the query. The intuition is that when, say,    $q$   is implied by document    $\Delta$  , then    $\Delta$   is assumed to be about    $q$  . Although retrieval based on this principle is possible, it is not enough. Typically, a query is not implied by any document leading to failure as in Boolean retrieval. To deal with this a number of things can be done. One is to weaken the implication, another is to attach a measure of uncertainty to implication. There is now a considerable literature on this starting with Van Rijsbergen (1986), culminating in Crestani  et al.  (1998). It is especially worth looking at Nie and Lepage (1998), which gives a broader introduction to the ‘logic in IR’, but nevertheless is in the same spirit as this chapter.  

Let us begin with the class of projectors (projection operators, or simply projections) on a Hilbert space  H . These are self-adjoint linear operators which are idempotent,   that is,  

$$
\mathbf{E}=\mathbf{E}^{*}=\mathbf{E}^{2}.
$$  

With each projector    $\mathbf{E}$  , is associated the subspace  

$$
\small\{\mathbf{\underline{{E}}}\}=\{\underline{{\mathbf{x}}}\mid\mathbf{\underline{{E}}}\underline{{\mathbf{x}}}=\underline{{\mathbf{x}}},\underline{{\mathbf{x}}}\in\mathbf{H}\}.
$$  

Any projector    $\mathbf{E}$   has exactly two eigenvalues, namely 1 and 0. These can be interpreted as the truth values of the proposition    $\mathbf{E}$  , or   $\left[\!\left[\mathbf{E}\right]\!\right]$  ], whichever is more convenient. If any self-adjoint transformation is now seen as a generalised ques- tion, or  observable , then it can be decomposed through the Spectral Theorem into a linear combination of questions,  

$$
\mathbf{A}=\alpha_{1}\mathbf{E}_{1}+\alpha_{2}\mathbf{E}_{2}+\cdot\cdot\cdot+\alpha_{k}\mathbf{E}_{k},{\mathrm{~where~}}\mathbf{E}_{i}\mathbf{E}_{j}=0{\mathrm{~for~}}i\neq j.
$$  

It is well known that the class of projectors on a Hilbert space make up an orthomodular lattice (or modular if ﬁnite) (Holland, 1970). The order relation is given by  

$$
\mathbf{E}\leq\mathbf{F}\;\mathrm{if}\;\mathrm{and}\;\mathrm{only}\;\mathrm{if}\;\mathbf{FE}=\mathbf{E},
$$  

that is,  

#  $\forall\underline{{\underline{{\mathbf{X}}}}}\in\underline{{\mathbf{H}}}$   we have that    $\mathbf{F}\mathbf{E}_{\underline{{\mathrm{X}}}}=\mathbf{E}_{\underline{{\mathrm{X}}}}$  .  

What we have done here is give  $\mathbf{E}\leq\mathbf{F}$   an algebraic character is ation, namely

  $\mathbf{F}\mathbf{E}=\mathbf{E}$  . We can similarly characterise algebraically, when    $\mathbf{E}$   and  $\mathbf{F}$   commute

  $(\mathbf{EF}=\mathbf{FE})$  ),  

$$
\begin{array}{c}{{{\bf E}^{\perp}={\bf I}-{\bf E},}}\\ {{{\bf E}\wedge{\bf F}={\bf E}{\bf F},}}\\ {{{\bf E}\vee{\bf F}={\bf E}+{\bf F}-{\bf E}{\bf F},}}\end{array}
$$  

where    $\perp,\,\wedge,\,\vee$  are the usual lattice operations complement, meet and join (Davey and Priestley, 1990). In general  $\mathbf{E}$   and  $\mathbf{F}$   will not commute.  

Our main concern is to develop an algebraic character is ation of the condi- tional  ${\bf E}\rightarrow{\bf F}$   and to study its properties. Given the entailment relation    $\mathbf{E}\leq\mathbf{F}$  deﬁned by  $\mathbf{FE}=\mathbf{E}$   (Herbut, 1994), we deﬁne a new proposition    ${\bf E}\rightarrow{\bf F}$  , the conditional of  $\mathbf{E}$   and  $\mathbf{F}$   by (Hardegree, 1976)  

$$
\begin{array}{r l}&{\left\|\mathbf{E}\rightarrow\mathbf{F}\right\|=\left\{\underline{{\mathbf{x}}}\mid\mathbf{F}\mathbf{E}\underline{{\mathbf{x}}}=\mathbf{E}\underline{{\mathbf{x}}},\underline{{\mathbf{x}}}\in\mathbf{H}\right\}}\\ &{\qquad\qquad=\left\{\underline{{\mathbf{x}}}\mid\left(\mathbf{F}-\mathbf{I}\right)\mathbf{E}\underline{{\mathbf{x}}}=0,\underline{{\mathbf{x}}}\in\mathbf{H}\right\}}\\ &{\qquad\qquad=\{\underline{{\mathbf{x}}}\mid\mathbf{F}^{\perp}\mathbf{E}\underline{{\mathbf{x}}}=0,\underline{{\mathbf{x}}}=\mathbf{H}\};}\end{array}
$$  

we will call this the Subspace conditional (S-conditional). It is easy to show that  $[[\mathbf{E}\rightarrow\mathbf{F}]]$   → ] is in fact a subspace (Hardegree, 1976). It remains to investigate its properties and whether it has the character of an implication. First notice that when  $\mathbf{E}\leq\mathbf{F}$  ,  $\mathbf{E}$   entails  $\mathbf{F}$  , then    $\mathbf{F}\mathbf{E}_{\underline{{\mathrm{X}}}}=\mathbf{E}_{\underline{{\mathrm{X}}}}$   for all  $\underline{{\mathbf{X}}}\in\mathbf{H}$  ; hence   $\left\|\mathbf{E}\rightarrow\mathbf{F}\right\|=\mathbf{H}$   →  = , or lattice-theoretically    $\mathbf{E}\rightarrow\mathbf{F}=\mathbf{I}$   since   $[[\![\mathbf{I}]\!]=\mathbf{H}$   = . This corresponds to a well- known result in classical logic:  

$$
\begin{array}{r l}&{\mathbf{\beta}=\mathbf{A}\supset\mathbf{B}\;\mathrm{if}\;\mathrm{and}\;\mathrm{only}\;\mathrm{if}\;\mathbf{A}\;\models\mathbf{B},}\end{array}
$$  

or lattice-theoretically  

$$
\mathbf{A}\to\mathbf{B}=\mathbf{I}{\mathrm{~if~and~only~if~}}\mathbf{A}\leq\mathbf{B}.
$$  

Thus the conditional    $\mathbf{A}\rightarrow\mathbf{B}$   is valid only in the case that  A  entails  B . We can interpret  $\mathbf{A}\rightarrow\mathbf{B}$   as the material conditional.  

Classically the Deduction Theorem also holds:  

$$
\begin{array}{r}{\mathbf{A}\,\&\,\mathbf{B}=\mathbf{C}\;\mathrm{if}\;\mathrm{and}\;\mathrm{only}\;\mathrm{if}\;\mathbf{A}\vDash\mathbf{C},}\\ {\mathbf{A}\wedge\mathbf{B}\le\mathbf{C}\;\mathrm{if}\;\mathrm{and}\;\mathrm{only}\;\mathrm{if}\;\mathbf{A}\le\mathbf{B}\to\mathbf{C}.}\end{array}
$$  

From this follows the distribution law, that is,  

$$
\mathbf{A}\wedge(\mathbf{B}\vee\mathbf{C})=(\mathbf{A}\wedge\mathbf{B})\vee(\mathbf{A}\wedge\mathbf{C}).
$$  

But the lattice of subspaces is not necessarily distributive and so the Deduction Theorem cannot hold for    ${\bf E}\rightarrow{\bf F}$  .  

Van Fraassen (1976) laid down some minimal conditions for any self- respecting connective   $\hookrightarrow'$   to satisfy  

$\mathbf{C}_{1}$   $\begin{array}{r l}&{\mathbf A\leq\mathbf B\Rightarrow\mathbf A\rightarrow\mathbf B=\mathbf I,}\\ &{\mathbf A\wedge(\mathbf A\rightarrow\mathbf B)\leq\mathbf B\,(\mathrm{modus~ponens}).}\end{array}$   $\mathbf{C}_{2}$  

Note that  

$$
\mathbf{A}\to\mathbf{B}=\mathbf{I}\Rightarrow\mathbf{A}\leq\mathbf{B}\ \mathrm{by}\ \mathbf{C}_{2},
$$  

and so  

$$
\mathbf{A}\leq\mathbf{B}\Leftrightarrow\mathbf{A}\rightarrow\mathbf{B}=\mathbf{I}.
$$  

In their earlier work, Nie and others have made a strong case that counterfactual conditionals are the appropriate implication connectives to use in IR (Nie  et al. , 1995). In the standard account of counterfactual conditionals (Lewis, 1973), the implication connective  $\hookrightarrow'$   does not satisfy the strong versions of transitivity, weakening and contraposition (Priest, 2001). These are  

$\begin{array}{r l}&{(\mathbf{A}\to\mathbf{B})\wedge(\mathbf{B}\to\mathbf{C})\leq(\mathbf{A}\to\mathbf{C}),}\\ &{\mathbf{A}\to\mathbf{C}\leq(\mathbf{A}\wedge\mathbf{B})\to\mathbf{C},}\\ &{\mathbf{A}\to\mathbf{B}=\mathbf{B}^{\perp}\to\mathbf{A}^{\perp}.}\end{array}$  

However, the weak versions are usually satisﬁed:  

$\mathbf{A}\to\mathbf{C}=\mathbf{I}\Rightarrow(\mathbf{A}\land\mathbf{B}\to\mathbf{C})=\mathbf{I},$  

The strong and weak forms of these laws are distinguished by statements con- cerning truth and validity. The weak form of transitivity says that if    $\mathbf{A}\rightarrow\mathbf{B}$  ,

  $\mathbf{B}\rightarrow\mathbf{C}$   are  valid  then so is    $\mathbf{A}\rightarrow\mathbf{C}$  . This is not the same as claiming that if

  $\mathbf{A}\rightarrow\mathbf{B}$  ,  $\mathbf{B}\rightarrow\mathbf{C}$   are  true  that    $\mathbf{A}\rightarrow\mathbf{C}$   is. Not surprisingly, the S-conditional satisﬁes the weak laws but not the strong ones. Any connective satisfying  $\mathbf{C}_{1}$  and  $\mathbf{C}_{2}$   can be shown to satisfy the weak forms WT, WW and WC. So, what about the S-conditional? It satisﬁes  

$$
\begin{array}{r l}&{\mathbf{C}_{1}\colon\quad\mathbf{E}\leq\mathbf{F}\Rightarrow\mathbf{E}\to\mathbf{F}=\mathbf{I},}\\ &{\mathbf{C}_{2}\colon\quad\mathbf{E}\wedge(\mathbf{E}\to\mathbf{F})\leq\mathbf{F}.}\end{array}
$$  

Proof:  

$\mathbf{C}_{1}$  : Suppose  $\mathbf{E}\leq\mathbf{F}$  ; then for all x,  $\mathbf{F}\mathbf{E}_{\underline{{\mathrm{X}}}}=\mathbf{E}_{\underline{{\mathrm{X}}}}$   by deﬁnition, also by deﬁnition we have that  $\left[\left[\mathbf{E}\rightarrow\mathbf{F}\right]\right]=\mathbf{H},$   →  = , which implies that    $\mathbf{E}\rightarrow\mathbf{F}=\mathbf{I}$  .

  $\mathbf{C}_{2}$  : Suppose x satisﬁes    $\mathbf{E}$   and  ${\bf E}\rightarrow{\bf F}$  , that is   $\underline{{\mathbf{\deltaX}}}\in\left[\!\left[\mathbf{E}\right]\!\right]$  ], or    $\mathbf{E}_{\underline{{\mathbf{X}}}}=\underline{{\mathbf{X}}}$  , similarly  $(\mathbf{E}\to\mathbf{F})\underline{{\underline{{\mathbf{x}}}}}=\underline{{\underline{{\mathbf{x}}}}}$  , but the latter is true if and only if    $\mathbf{F}\mathbf{E}_{\underline{{\mathrm{X}}}}=\mathbf{E}_{\underline{{\mathrm{X}}}}$   by deﬁnition. But we already have that    $\mathbf{E}_{\underline{{\mathbf{X}}}}=\mathbf{\underline{{X}}}$  , therefore    $\mathbf{F}_{\underline{{\mathbf{X}}}}=\mathbf{\underline{{X}}}$   and   $\underline{{\boldsymbol{\mathrm{X}}}}$   satisﬁes    $\mathbf{F}$  , hence  $\mathbf{E}\wedge(\mathbf{E}\to\mathbf{F})\leq\mathbf{F}$  . QED.  

Thus  ${\bf E}\rightarrow{\bf F}$   is one of those conditionals that does not satisfy the strong versions of transitivity, weakening or contraposition but it does satisfy the weak forms.  

Let us summarise the situation thus far. The set of subspaces of a Hilbert space form a special kind of lattice (complete, atomic, orthomodular) which is not  distributive . The logical structure of this lattice is not Boolean or classical. The logical connectives    $\perp$  ,  ∧ ,    $\vee$  and    $\rightarrow$  in terms of subspace operations are deﬁned as:  

$\left[\!\!\left[\mathbf{E}\wedge\mathbf{F}\right]\!\!\right]\!=\!\left[\!\!\left[\mathbf{E}\right]\!\!\right]\cap\left[\!\!\left[\mathbf{F}\right]\!\!\right]$   ∧  =  ∩ ], a set-theoretic intersection which is again a subspace.  $[\![\mathbf{E}^{\perp}]\!]=\left[\![\mathbf{E}]\!\right]^{\perp}$   = , the set of vectors which is orthogonal to    $\mathbf{E}$   which form a subspace.  $[\![\mathbf{E}\vee\mathbf{F}]\!]=[\![\mathbf{E}]\!]\oplus[\![\mathbf{F}]\!]$   ∨  =  ⊕ ], the closure of all linear combinations of  $\underline{{\mathbf{\deltaX}}}\in\left[\!\!\left[\mathbf{E}\right]\!\!\right]$  and   $\mathbf{y}\in\left[\![\mathrm{F}]\!\right]\!$  ] which again forms a subspace.  $\left\|\mathbf{E}\rightarrow\bar{\mathbf{F}}\right\|=\left\{\mathrm{x}\mid\mathbf{F}\mathbf{E}_{\underline{{\mathrm{X}}}}=\mathbf{E}_{\underline{{\mathrm{X}}}},\underline{{\mathrm{X}}}\in\mathbf{H}\right\}$  .  

It turns out that an example of    ${\bf E}\rightarrow{\bf F}$   can be given in closed form, namely  

$$
\mathbf{E}\to\mathbf{F}=\mathbf{E}^{\perp}\lor(\mathbf{E}\land\mathbf{F}),
$$  

which is known as the Sasaki hook; and there are many others, see Mittelstaedt (1972)). With this interpretation the semantics of    ${\bf E}\rightarrow{\bf F}$   is given by  

$$
[\![\mathbf{E}\rightarrow\mathbf{F}]\!]=\left[\![\mathbf{E}]\!]^{\perp}\oplus(\![\mathbf{E}]\!]\cap\left[\![\mathbf{F}]\!\right]).\right.
$$  

The connectives introduced are not truth-functional. This is easy to see for negation and disjunction. Clearly   $[\![\mathbf{E}^{\perp}]\!]\oplus[\![\mathbf{E}]\!]=\mathbf{H}.$   ⊕  = . This means that there are vectors  $\underline{{\mathbf{X}}}\in\mathbf{H}$   which satisfy neither  $\mathbf{E}^{\perp}$  nor  E , but do satisfy    $\mathbf{E}^{\perp}\lor\mathbf{E}$  , making  $\perp$  a ‘choice negation’. Similarly, since   $[[\mathbf{E}\ \vee\ \mathbf{F}]]$   ∨ ] is the closure of   $\underline{{\boldsymbol{\mathbf{X}}}}+\boldsymbol{\mathbf{\check{y}}}$  , where  $\underline{{\mathbf{\deltaX}}}\in\left[\!\!\left[\mathbf{E}\right]\!\!\right]$  ] and  $\underline{{\mathbf{y}}}\in\left[\![\mathbf{F}]\!\right]$  ], it describes a ‘choice disjunction’.  

# Compatibility  

To see how the non-classical S-conditional relates to the classical material implication we need to re-introduce the notion of compatibility. Remember that we previously deﬁned the compatibility of two projectors    $\mathbf{E}$   and    $\mathbf{F}$   by  $\mathbf{EP}=\mathbf{F}\mathbf{E}$  . This time we take a general lattice-theoretical approach. On any orthomodular lattice we can deﬁne  

$$
\mathbf{A}\to\mathbf{B}=\mathbf{A}^{\perp}\lor(\mathbf{A}\land\mathbf{B}).
$$  

It is easy to prove that (see Hardegree, 1976) that the minimal conditions  $\mathbf{C}_{1}$   and  $\mathbf{C}_{2}$   are satisﬁed. Moreover   $\mathbf{C}_{2}$  , modus ponens, is equivalent to the  orthomodular law  for lattices:  

$$
\mathbf{A}\leq\mathbf{B}\Rightarrow\mathbf{B}\land(\mathbf{B}^{\perp}\land\mathbf{A})\leq\mathbf{A}.
$$  

We are now ready to deﬁne our relation  $K$   of compatibility:  

$$
\mathbf{A}K\mathbf{B}{\mathrm{~if~and~only~if~}}\mathbf{A}=(\mathbf{A}\wedge\mathbf{B})\vee(\mathbf{A}\wedge\mathbf{B}^{\perp}).
$$  

Any ortho complemented lattice is orthomodular if the relation  $K$   is symmetric:

  $\mathbf{A}K\mathbf{B}=\mathbf{B}K\mathbf{A}$  . The lattice is Boolean if the relation    $K$   is universal, that is,

 ‘compatibility rules OK’. The S-conditional  

$$
\begin{array}{r l}{\mathbf{A}\to\mathbf{B}=\mathbf{A}^{\perp}\lor(\mathbf{A}\land\mathbf{B})}&{{}}\\ {=\mathbf{A}^{\perp}\lor\mathbf{B}}&{{}}\end{array}
$$  

when  A K B . In other words, the S-conditional defaults to the material condi- tional when the two elements of the lattice are compatible. Since the lattice of subspaces of a Hilbert space form an orthomodular lattice this holds for  ${\bf E}\rightarrow{\bf F}$  , where  $\mathbf{E}$   and    $\mathbf{F}$   are projectors. To prove the default result is non-trivial (see Holland, 1970), and depends on the connection between compatibility and distributivity:  

$$
\mathbf{A}K\mathbf{B}{\mathrm{~and~}}\mathbf{A}K\mathbf{C}\Rightarrow\{\mathbf{A},\mathbf{B},\mathbf{C}\}
$$  

(Remember that the lattice of Hilbert subspaces is not distributive.) Now since

  ${\bf A}K{\bf A}^{\perp}$  and if  $\mathbf{A}K\mathbf{B}$  , then  

$$
\begin{array}{r l}&{\mathbf{A}\rightarrow\mathbf{B}=\mathbf{A}^{\perp}\wedge(\mathbf{A}\wedge\mathbf{B})}\\ &{\qquad\qquad=(\mathbf{A}^{\perp}\vee\mathbf{A})\wedge(\mathbf{A}^{\perp}\vee\mathbf{B})}\\ &{\qquad\qquad=\mathbf{I}\wedge(\mathbf{A}^{\perp}\vee\mathbf{B})}\\ &{\qquad\qquad=\mathbf{A}^{\perp}\vee\mathbf{B}.}\end{array}
$$  

The main reason for examining the conditions for compatibility and distribution is that if IR models are to be developed within a general vector (Hilbert) space frame-work, then without further empirical evidence to the contrary it has to be assumed that the subspace logic will be non-classical and in general fails the law of distribution. The failure can be seen as coming about because of the lack of compatibility between propositions, to be represented by subspaces in a Hilbert space. Accepting that subspaces are ‘ﬁrst class objects’, we interpret the class of objects about something, as a subspace, and similarly, the class of relevant objects at any point in time is seen as a subspace. So we have moved from considering ‘subsets’, via ‘artiﬁcial classes’ to subspaces as ﬁrst class objects whose relationships induce logics.  

If  R  is the projector on the subspace of relevant objects, and  E  is the projector onto the subspace of objects about the observable    $\mathbf{E}$   (a yes/no property) then compatibility means that  

$$
\mathbf{R}=(\mathbf{R}\wedge\mathbf{E})\vee(\mathbf{R}\wedge\mathbf{E}^{\perp}).
$$  

Here is the nub of our non-classical view, namely that the disjunction is not necessarily classical. In simple IR terms an object may be about some topic or its negation once observed, but before observation it may be neither. Interpreting the compatibility, or lack of it, we assumed that    $\mathbf{RE}\neq\mathbf{ER}$  , which means that observing relevance followed by topicality is not the same as observing topicality followed by relevance.  

Compatibility for projectors about topicality may also fail. If we have two projectors  $\mathbf{E}_{1}$   and    $\mathbf{E}_{2}$   that are not compatible then  

$$
\mathbf{E}_{2}\neq(\mathbf{E}_{2}\wedge\mathbf{E}_{1})\vee(\mathbf{E}_{2}\wedge\mathbf{E}_{1}^{\perp}).
$$  

we can say  t    $\mathbf{E}_{1}\mathbf{E}_{2}\neq\mathbf{E}_{2}\mathbf{E}_{1}$  , that is obse ng that an ob t is about  $\mathbf{E}_{1}$   followed by  E  is not the same as observing  E  followed by  E . With the assumption of stochastic independence in Bayesian updating, the observation of  $\mathbf{E}_{1}$   followed by  $\mathbf{E}_{2}$   has the same impact on computing the posterior probability as the reverse. But, in general one would expect   $\mathrm{P}(\mathrm{H}\mid\mathbf{E}_{1},\mathbf{E}_{2})\neq\mathrm{P}(\mathrm{H}\mid\mathbf{E}_{2},\mathbf{E}_{1})$  , as is of course the case in Jeffrey conditional is ation (Jeffrey, 1983).  

# Stalnaker conditional  

There is a well-known conditional in the philosophical literature which fails to satisfy ST, SW and SC, and this is the Stalnaker conditional (Stalnaker, 1970, Lewis, 1976, Van Fraassen, 1976 and Harper  et al. , 1981). It was the motivation behind a series of papers that explored its application in information retrieval (Crestani  et al. , 1998). We next show that the S-conditional is a Stalnaker conditional, an important connection to make since it links much of the analysis in the previous pages with previous work in IR.  

To show it we need to introduce possible world analysis (Priest, 2001). Remember that our propositions are subspaces in a Hilbert space and that cor- responding to each subspace is a projector onto it. A world in this setup is identiﬁed with a vector  $\underline{{\mathbf{X}}}\in\mathbf{H}$  . On this Hilbert space we have a distance func- tion between any two vectors   $\underline{{\mathbf{X}}}$   and y given by the inner product  

$$
d(\underline{{\mathrm{x}}},\underline{{\mathrm{y}}})=\sqrt{(\underline{{\mathrm{x}}}-\underline{{\mathrm{y}}},\underline{{\mathrm{x}}}-\underline{{\mathrm{y}}})}=\|\underline{{\mathrm{x}}}-\underline{{\mathrm{y}}}\|.
$$  

Now the deﬁnition of a Stalnaker conditional goes as follows. We deﬁne a family of selection functions on    $\mathbf{H}$  , called Stalnaker selection functions. If    $S_{A}$  is such a function for proposition  $\mathbf{A}$  , then  $S_{A}(\underline{{\mathbf{x}}})$   denotes the ‘nearest’ world to  $\underline{{\boldsymbol{\mathbf{X}}}}$   in which    $\mathbf{A}$   is satisﬁed. Intuitively a counterfactual    $\textbf{A}>\textbf{B}$   is true in world  only when the nearest  A -world to  is also a    $\mathbf{B}$  -world. By an    $\mathbf{A}(\mathbf{B})$  -  $\underline{{\boldsymbol{\mathrm{X}}}}$   $\underline{{\boldsymbol{\mathbf{X}}}}$  world we of course mean the world at which    $\mathbf{A}(\mathbf{B})$   is true. We have used   $^{*}{>}^{\backprime}$  for our implication because we do not have a semantics for it yet. This is given by  

$$
\underline{{\mathbf{\Pi}}}\in\left[\!\left[\mathbf{A}>\mathbf{B}\right]\!\right]\mathrm{if~and~only~if}\:S_{A}(\underline{{\mathbf{\Pi}}})\in\left[\!\left[\mathbf{B}\right]\!\right]\!.
$$  

To ensure that   $^{*}{>}^{\backprime}$   is a respectable implication satisfying   $\mathbf{C}_{1}$   and  $\mathbf{C}_{2}$   a number of technical restrictions (mostly obvious) are placed on it (see Stalnaker, 1970, or Lewis, 1976, for details).  

$\mathbf{R}_{1}$  :  $S_{A}(\underline{{\mathbf{x}}})\in\mathbb{[\mathbf{A}]},$  ,  $\mathbf{R}_{2}$  :  $\underline{{\mathbf{\Pi}}}_{\underline{{\mathbf{X}}}}\in\mathbb{[A]}\Rightarrow S_{A}(\underline{{\mathbf{x}}})=\underline{{\mathbf{x}}},$   ${\bf R}_{3}$  :  $S_{A}(\underline{{\mathbf{x}}})\in\left[\![\mathbf{B}]\!\right]$  ] and  $S_{B}(\underline{{\mathbf{x}}})=\left[\!\!\left[\mathbf{A}\right]\!\!\right]\Rightarrow S_{A}(\underline{{\mathbf{x}}})=S_{B}(\underline{{\mathbf{x}}}).$   ⇒  =  

A technical convenience condition requires that whenever    $S_{A}(\underline{{\mathbf{x}}})$   does not exist, that is, there is no nearest  A -world to  $\underline{{\mathbf{X}}}$  , then  $S_{A}(\underline{{\mathbf{x}}})=\theta$  , the absurd world.  

Hardegree (1976) introduced what he called the ‘canonical selection func- tion’ by interpreting the foregoing entirely within a Hilbert space. The most important aspect of his interpretation is that  

$$
S_{A}(\underline{{\mathbf{x}}})=\mathbf{A}_{\underline{{\mathbf{x}}}},
$$  

where  A  is the proposition corresponding to, or the projection from    $\mathbf{H}$   onto, the subspace  $[\![\mathbf{A}]\!]$  ]. The claim is made that within a Hilbert space the nearest vector

  $\mathbf{y}\in\left[\!\!\left[\mathbf{A}\right]\!\!\right]$  ] to any vector  $\underline{{\mathbf{X}}}\in\mathbf{H}$   is given by    $\mathbf{Ax}_{-}$   with respect to the distance function

  $\overline{d}(\underline{\mathrm x},\underline{\mathrm y})=\|\underline{\mathrm x}-\underline{\mathrm y}\|$  deﬁned previously. It is instructive to set out the proposition and see a proof. To be proved is that for all y for which    $\mathbf{A}\underline{{\mathbf{y}}}=\underline{{\mathbf{y}}}\mathbf{\Pi}(\underline{{\mathbf{y}}}\in\mathbb{[\mathbf{A}]})$  ]) the nearest (unique) vector closest to   $\underline{{\boldsymbol{\mathrm{X}}}}$   is  A x. It is enough to show that for y such that    $\mathbf{A}\underline{{\mathbf{y}}}=\underline{{\mathbf{y}}}$   we have  

$$
\mathrm{(\underline{{x}}-A\underline{{x}},\underline{{x}}-A\underline{{x}})<(\underline{{x}}-\underline{{y}},\underline{{x}}-\underline{{y}})\,u n l e s s\,A\underline{{x}}=\underline{{y}}}.
$$  

There are many ways of proving it, but possibly the most elementary is to start with the following (by deﬁnition):  

$$
\begin{array}{r}{\mathrm{for~all~\underline{{x}},(\underline{{x}},\underline{{x}})>0~u n l e s s~\underline{{x}}=\theta,~}}\\ {\mathrm{s~(\mathbf{A}\underline{{x}}-\underline{{y}},\mathbf{A}\underline{{x}}-\underline{{y}})>0~u n l e s s~\mathbf{A}\underline{{x}}-\underline{{y}}=\theta,~\mathrm{or}~\mathbf{A}\underline{{x}}=\underline{{y}}.}\end{array}
$$  

We can transform this last equation into the equation to be proved as follows:  

$$
\begin{array}{c}{(\mathbf{A}_{\underline{{X}}}-\underline{{y}},\mathbf{A}_{\underline{{X}}}-\underline{{y}})>0,}\\ {(\mathbf{A}_{\underline{{X}}},\mathbf{A}_{\underline{{X}}})-(\mathbf{A}_{\underline{{X}}},\underline{{y}})-(\underline{{y}},\mathbf{A}_{\underline{{X}}})+(\underline{{y}},\underline{{y}})>0,}\end{array}
$$  

Adding  

$$
(\mathtt{X},\mathtt{X})-(\mathtt{X},\mathtt{X})-2(\mathtt{A}\mathtt{X},\mathtt{A}\mathtt{X})+(\mathtt{A}\mathtt{X},\mathtt{X})+(\mathtt{X},\mathtt{A}\mathtt{X})=0
$$  

to both sides, but note that  

$$
(\mathbf{A}_{\underline{{\mathbf{x}}}},{\underline{{\mathbf{x}}}})=({\underline{{\mathbf{x}}}},\mathbf{A}_{\underline{{\mathbf{x}}}})=(\mathbf{A}_{\underline{{\mathbf{x}}}},\mathbf{A}_{\underline{{\mathbf{x}}}})
$$  

$$
\mathrm{because}\,\mathbf{A}=\mathbf{A}^{*}\,\mathrm{and}\,\mathbf{A}=\mathbf{A}^{2},
$$  

we obtain  

$$
\begin{array}{r l}&{(\underline{{\mathbf{x}}},\underline{{\mathbf{x}}})-(\underline{{\mathbf{x}}},\mathbf{A}\underline{{\mathbf{x}}})-(\mathbf{A}\underline{{\mathbf{x}}},\underline{{\mathbf{x}}})+(\mathbf{A}\underline{{\mathbf{x}}},\mathbf{A}\underline{{\mathbf{x}}})<(\underline{{\mathbf{x}}},\underline{{\mathbf{x}}})-(\mathbf{A}\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})-(\underline{{\mathbf{y}}},\mathbf{A}\underline{{\mathbf{x}}})+(\underline{{\mathbf{y}}},\underline{{\mathbf{y}}}).}\\ &{\qquad\qquad\qquad\mathrm{8it}\,(\mathbf{A}\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})=(\underline{{\mathbf{x}}},\mathbf{A}\underline{{\mathbf{y}}})=(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})\,\mathrm{because}\,\mathbf{A}\underline{{\mathbf{y}}}=\underline{{\mathbf{y}}},}\\ &{\qquad\qquad\mathrm{and}\,(\underline{{\mathbf{y}}},\mathbf{A}\underline{{\mathbf{x}}})=(\mathbf{A}\underline{{\mathbf{y}}},\underline{{\mathbf{x}}})=(\underline{{\mathbf{y}}},\underline{{\mathbf{x}}})\,\mathrm{because}\,\mathbf{A}\underline{{\mathbf{y}}}=\underline{{\mathbf{y}}};}\end{array}
$$  

we get  

$$
\begin{array}{r l}&{(\underline{{\mathbf{x}}},\underline{{\mathbf{x}}})-(\underline{{\mathbf{x}}},\mathbf{A}\underline{{\mathbf{x}}})-(\mathbf{A}\underline{{\mathbf{x}}},\underline{{\mathbf{x}}})+(\mathbf{A}\underline{{\mathbf{x}}},\mathbf{A}\underline{{\mathbf{x}}})<(\underline{{\mathbf{x}}},\underline{{\mathbf{x}}})-(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})-(\underline{{\mathbf{y}}},\underline{{\mathbf{x}}})+(\underline{{\mathbf{y}}},\underline{{\mathbf{y}}})}\\ &{\operatorname{unless}\mathbf{A}\underline{{\mathbf{x}}}=\underline{{\mathbf{y}}},}\end{array}
$$  

which is the same as  

$$
\mathrm{(\underline{{x}}-A\underline{{x}},\underline{{x}}-A\underline{{x}})<(\underline{{x}}-\underline{{y}},\underline{{x}}-\underline{{y}})u n l e s s\,A\underline{{x}}=\underline{{y}}},
$$  

which was to be proved (Hardegree, 1976).  

This establishes that our canonical selection function is a simple function indeed; to map   $\underline{{\mathbf{X}}}$   to the nearest  A -world we project  $\underline{{\mathbf{X}}}$   onto   $[\![\mathbf{A}]\!]$  ] using the projector  A .  

Now, drawing it together, we can write down the semantics for the S- conditional and the Stalnaker conditional as follows:  

$$
\begin{array}{r l}&{~~~~S_{A}(\underline{{\mathbf{x}}})=\mathbf{A}\underline{{\mathbf{x}}},}\\ &{~~~~[\![\mathbf{A}>\mathbf{B}]\!]=\{\underline{{\mathbf{x}}}~|~\mathbf{A}\underline{{\mathbf{x}}}\in[\![\mathbf{B}]\!],\underline{{\mathbf{x}}}\in\mathbf{H}\}}\\ &{~~~~~~~~~~~~~~~~~~=\{\underline{{\mathbf{x}}}~|~\mathbf{B}\mathbf{A}\underline{{\mathbf{x}}}=\mathbf{A}\underline{{\mathbf{x}}}\},}\\ &{~~~~~~~~~~~~~~~~~~[\![\mathbf{A}\to\mathbf{B}]\!]=\{\underline{{\mathbf{x}}}~|~\mathbf{B}\mathbf{A}\underline{{\mathbf{x}}}=\mathbf{A}\underline{{\mathbf{x}}}\}}\\ &{~~~~~~~~~~~~~~~~~~=[\![\mathbf{A}^{\perp}\lor(\mathbf{A}\land\mathbf{B})]\!].}\end{array}
$$  

From this we conclude that  

$$
\mathbf{A}>\mathbf{B}=\mathbf{A}\rightarrow\mathbf{B}=\mathbf{A}^{\perp}\vee(\mathbf{A}\wedge\mathbf{B}).
$$  

We have shown that the Stalnaker conditional and the S-conditional are the same thing. At this point we could go on to describe how to construct the probability of a conditional. Stalnaker (1970) did this by claiming it was best modelled as a conditional probability, which was shown by Lewis (1976) to be subject to a number of triviality results. Lewis then showed how through  imaging  one could calculate the probability of a conditional that was not subject to those triviality results. Van Rijsbergen (1986) conjectured that imaging would be the correct way to handle the probability of a conditional for IR. Subsequently this was explored further by Crestani and Van Rijsbergen (1995) in a series of papers. However, given the way that a conditional can be given a semantics in a vector space, we can use our results so far to calculate the probability associated with a conditional via Gleason’s Theorem using the trace function. This will be done in the next chapter.  

# Further reading  

A formal connection is made between conditional logic and quantum logic which enables a conditional logic to be interpreted in Hilbert space (or vector space). Hitherto this has not been possible. Some of the earliest papers argu- ing for this connection are by Hardegree (1975, 1976, 1979) and by Lock and Hardegree (1984). In IR a recommendation for using a form of the Stalnaker conditional for counterfactual reasoning was given by Van Rijsbergen (1986), followed by a more detailed analysis by Nie and Brisebois  et al.  (1995) and Nie and Lepage (1998). It is interesting that conditional logic has emerged as an important area of research for IR. The fact that non-classical logics have been developed independently in quantum mechanics is very convenient, espe- cially given the relationship between them and conditional logic described by Hardegree. It means that we can translate the relevant logical statements into algebraic calculations in Hilbert space, using results from quantum mechan- ics to guide us, and intuitions from IR to construct the appropriate algebraic form.  

There is an extensive philosophical literature on conditional logic, for exam- ple, Stalnaker (1970), Lewis (1973), Putnam (1975, 1981), Friedman and Putnam (1978), Gibbins (1981), Bub (1982), Stairs (1982) and Bacciagaluppi (1993). It makes useful reading before attempting to apply conditional logic to IR problems. Research on quantum logics emerged from the seminal paper by Birkhoff and Von Neumann (1936) and has been active ever since. The quantum logics literature is important for IR because it demonstrates how to interpret such logics in vector spaces and also how to associate appropriate probabil- ity measures with them (Halpin, 1991). There are several good bibliographies on quantum logics, for example, in Suppes (1976), Pavicic (1992) and R´ edei (1998). To obtain an overview of the subject it is recommended that one read parts of Beltrametti and Cassinelli (1981), Beltrametti and Van Fraassen (1981), Garden (1984) and R´ edei (1998). More specialised development of such logics can be found in Kochen and Specker (1965a), Heelan (1970a,b), Mittelstaedt

 (1972), Greechie and Gudder (1973), Finch (1975), Piron (1977) and Pitowsky

 (1989).  

In the light of the Spectral Theorem demonstrated in Chapter 4, it is clear that an observable can be reduced to a set of yes/no questions. This is explored in detail by Beltrametti and Cassinelli (1977) and Hughes (1982). The relationship between quantum logic and probability has been investigated in detail by K¨ agi- Romano (1977), Bub (1982) and Pitowsky (1989). Logicians have always be interested in non-standard logics (Priest, 2001), often with a sceptical view, see, for example, Dalla Chiara (1986, 1993). More recently computer scientists have shown an interest (Rom´ an, 1994 and Engesser and Gabbay, 2002). The relationship between classical and quantum logic is explored by Piron (1977) and Heelan (1970a).  

Finally, the most thorough explanation of logics associated with Hilbert spaces remains Varadarajan (1985). There is now an interesting article by the same author describing some of the historical context (Varadarajan, 1993).  

# 6 The geometry of IR  

‘Let no man enter here who is ignorant of geometry’  

Plato 1  

In the previous chapters we have introduced set-theoretic, logical and algebraic notions, all of which can be used proﬁtably in IR. We now wish to broaden the discussion somewhat and attempt to introduce a  language  and a  notation for handling these disparate notions within a single space, viz. Hilbert space (Simmons, 1963), thereby constructing a probability measure on that space via its geometry. At ﬁrst glance this appears to be a difﬁcult task, but if we consider that much IR research has been modelled in ﬁnite vector spaces (Salton, 1968) with an inner product, many of our intuitions for the inner product can be transferred to the discussion based on Hilbert spaces. One major reason for adopting the more abstract point of view is that we wish to present a ‘language’ for describing and computing objects,whethertext,imageorspeech,inageneral way before considering any particular implementation.  

The language introduced uses a small set of operators and functions, and the notation will be the Dirac notation (Dirac, 1958). Although at ﬁrst sight the Dirac notation strikes one as confusing and indeed awkward for learning about linear algebra, its use in calculating or computing simple relationships in Hilbert space is unparalleled.   Its great virtues are that any calculation is simple, the meaning is transparent, and many of the ‘housekeeping’ rules are automatically taken care of. We will demonstrate these virtues as we progress.  

So, to begin with we will assume that any object of interest, e.g. a doc- ument, an image or a video clip, is represented by a normalised vector (one of unit length) in an abstract Hilbert space of ﬁnite dimension. Extension to an inﬁnite-dimensional space would not be difﬁcult but would add unnec- essary complications at this point. Later it will be more convenient to rep- resent an object by the projector on to a 1-dimensional Hilbert space, known as a ray. Unless speciﬁed otherwise, the Hilbert space will be assumed to be complex, that is, the scalars will be complex numbers. It is possible and likely that the extra representation power achieved through complex numbers may be of some use in the future. In any case measurement outcomes are always assumed to be real.  

# Preliminaries: D-notation  

To begin with we have that each vector in space    $\mathbf{H}$   is representable by a ket, thus w.r.t. the canonical basis,  

$$
|\underline{{{\bf x}}}\rangle=\left(\begin{array}{c}{{x_{1}}}\\ {{.}}\\ {{.}}\\ {{.}}\\ {{x_{n}}}\end{array}\right).
$$  

On this space of vectors it is possible to deﬁne a linear function  $F$   mapping each vector into a scalar. A general result is that such linear functionals are in 1:1 correpondence with the vectors in the space (Riesz and Nagy, 1990), and that  $F(\underline{{\mathbf{x}}}))=\alpha$   can be uniquely represented by  

$$
F(\underline{{\mathbf{x}}})=\langle\underline{{\mathbf{y}}}\mid\underline{{\mathbf{x}}}\rangle,
$$  

an inner product.   For example, imagine we had a linear function, mapping each document in a space into a real number, then that mapping can be represented by ﬁnding a vector  $\underline{{\boldsymbol{\mathrm{y}}}}$   for which    $\langle\underline{{\mathbf{y}}}\mid\underline{{\mathbf{x}}}\rangle$  is equal to the value of    $F$   at each    $\left|\underline{{\mathbf{X}}}\right\rangle$  . Implicitly we are using this when we calculate the cosine correlation between a query vector and any document. If we had a linear function producing a value for each document, then the operation of the function is representable as an inner product between a query vector and each document.  

This 1:1 correspondence between linear functionals and vectors leads to the implementation of the inner product    $\langle\underline{{y}}\mid\underline{{x}}\rangle$  by representing    $\langle\underline{{\mathbf{y}}}|$   as the conjugate transpose of    $|\underline{{\mathbf{y}}}\rangle$  , that is  

$$
\langle{\underline{{\mathbf{y}}}}|={\left(\begin{array}{l}{y_{1}}\\ {\ \cdot}\\ {\ \cdot}\\ {\ \cdot}\\ {y_{n}}\end{array}\right)}^{*}=({\overline{{y}}}_{1}\cdot\cdot\cdot{\overline{{y}}}_{n}).
$$  

Thus  

$$
\langle\underline{{\mathbf{y}}}\,|\,\underline{{\mathbf{x}}}\rangle=\sum_{i=1}^{n}\overline{{y}}_{i}x_{i}
$$  

w.r.t. the canonical basis.  

Given the canonical basis of orthonormal vectors    $\{\underline{{\mathbf{e}}}_{1},\;\underline{{\mathbf{e}}}_{2},\;.\;.\;.\;,\;\underline{{\mathbf{e}}}_{n}\}$   for a Hilbert space    $\mathbf{H}$  , then the orthonormality condition is easily stated as

  $\langle\underline{{\mathbf{e}}}_{i}\mid\underline{{\mathbf{e}}}_{j}\rangle\,=\,\delta_{i j}$  pendent vectors deﬁning a basis

  $\{\underline{{\mathrm{f}}}_{1},\,\underline{{\mathrm{f}}}_{2},\,.\,.\,.\,\,,\,\underline{{\mathrm{f}}}_{n}\}$  { }  we can write  ⟨  $\langle\underline{{\mathbf{f}}}_{i}\mid\underline{{\mathbf{f}}}_{j}\rangle=g_{i j}$   | . This c hange the representation of vectors and matrices in one system  {  $\{\underline{{\mathrm{f}}}_{1},\underline{{\mathrm{f}}}_{2},\.\.\ .\ ,\underline{{\mathrm{f}}}_{n}\}$  }  to one in  $\{\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2},.\ .\ .\ ,\underline{{\mathbf{e}}}_{n}\}$   and vice versa (Sadun, 2001).  

Having deﬁned an  inner  product between vectors it is possible to deﬁne an outer  product. In the Dirac notation an outer product is deﬁned, as one might expect, as    $\lvert\underline{{\mathbf{y}}}\rangle\,\langle\underline{{\mathbf{x}}}\rvert$  . Before giving a formal deﬁnition, observe that in the matrix representation  

$$
\begin{array}{r l}{|\underline{{y}}\rangle\langle\underline{{x}}|=\left(\begin{array}{l}{y_{1}}\\ {.}\\ {.}\\ {y_{n}}\end{array}\right)(\overline{{x}}_{1}}&{.\ldots}&{.\overline{{x}}_{n})}\\ {=\left(\begin{array}{l l l l l}{y_{1}\overline{{x}}_{1}}&{y_{1}\overline{{x}}_{2}}&{.}&{.}&{y_{1}\overline{{x}}_{n}}\\ {y_{2}\overline{{x}}_{1}}&{.}&{.}&{.}&{.}\\ {.}&{.}&{.}&{.}&{.}\\ {y_{n}\overline{{x}}_{1}}&{.}&{.}&{.}&{y_{n}\overline{{x}}_{n}}\end{array}\right).}\end{array}
$$  

For example, in a 5-dimensional space  

$$
|\underline{{{\sf e}}}_{i}\rangle\langle\underline{{{\sf e}}}_{j}|=\left(\begin{array}{l}{0}\\ {0}\\ {1}\\ {0}\\ {0}\end{array}\right)(0\begin{array}{l l l l l}{~}&{1}&{0}&{0}&{0}\end{array})=\left(\begin{array}{l l l l l}{0}&{0}&{0}&{0}&{0}\\ {0}&{0}&{0}&{0}&{0}\\ {0}&{1}&{0}&{0}&{0}\\ {0}&{0}&{0}&{0}&{0}\\ {0}&{0}&{0}&{0}&{0}\end{array}\right).
$$  

Formally, for any two vectors x,  $\underline{{\mathbf{y}}}\in\mathbf{H}$   we deﬁne the operator    $\left|\underline{{\mathbf{y}}}\right\rangle\left\langle\underline{{\mathbf{x}}}\right|$   for any w by  

$$
(|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{x}}}|)\underline{{\mathbf{w}}}=|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{w}}}\rangle=\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{w}}}\rangle\,|\underline{{\mathbf{y}}}\rangle.
$$  

This has two interpretations, either it is the result of applying the operator  $|\underline{{\mathbf{y}}}\rangle\,\langle\underline{{\mathbf{x}}}|$  to the vector w, or the result of multiplying the vector y by the complex number  $\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{w}}}\rangle$  . Both interpretations are valid, and this illustrates beautifully how the Dirac notation looks after its own ‘housekeeping’.  

The map   $(\underline{{\mathbf{y}}},\underline{{\mathbf{x}}})\to|\underline{{\mathbf{y}}}\rangle\,\langle\underline{{\mathbf{x}}}|$   from  $\mathbf{H}\times\mathbf{H}$   into the set of bounded linear operators has the following properties (Parthasarathy, 1992, p. 5):  

(1)    $\lvert\underline{{\mathbf{y}}}\rangle\,\langle\underline{{\mathbf{x}}}\rvert$   is linear in y and conjugate linear in  $\underline{{\mathbf{X}}}$  , that is  

$$
\begin{array}{c c}{|\alpha_{1}\underline{{\underline{{\mathbf{y}}}}}_{1}+\alpha_{2}\underline{{\underline{{\mathbf{y}}}}}_{2}\rangle\langle\underline{{\mathbf{x}}}|=\alpha_{1}|\underline{{\underline{{\mathbf{y}}}}}_{1}\rangle\langle\underline{{\mathbf{x}}}|+\alpha_{2}|\underline{{\underline{{\mathbf{y}}}}}_{2}\rangle\langle\underline{{\mathbf{x}}}|,}&\\ {|\underline{{\underline{{\mathbf{y}}}}}\rangle\langle\beta_{1}\underline{{\underline{{\mathbf{x}}}}}_{1}+\beta_{2}\underline{{\mathbf{x}}}_{2}|=\overline{{\beta}}_{1}|\underline{{\underline{{\mathbf{y}}}}}\rangle\langle\underline{{\mathbf{x}}}_{1}|+\overline{{\beta}}_{2}|\underline{{\underline{{\mathbf{y}}}}}\rangle\langle\underline{{\mathbf{x}}}_{2}|.}&\\ {(|\underline{{\underline{{\mathbf{y}}}}}\rangle\langle\underline{{\mathbf{x}}}|)^{*}=|\underline{{\mathbf{x}}}\rangle\langle\mathbf{x}|.}&\\ {|\underline{{\underline{{\mathbf{y}}}}}_{1}\rangle\langle\underline{{\mathbf{x}}}_{1}||\underline{{\underline{{\mathbf{y}}}}}_{2}\rangle\langle\underline{{\mathbf{x}}}_{2}|\cdot\cdot\cdot|\underline{{\underline{{\mathbf{y}}}}}_{n}\rangle\langle\underline{{\mathbf{x}}}|=\left\{\prod_{i=1}^{n-1}\langle\underline{{\mathbf{x}}}_{i}|\underline{{\mathbf{y}}}_{i+1}\rangle\right\}|\underline{{\underline{{\mathbf{y}}}}}_{1}\rangle\langle\underline{{\mathbf{x}}}_{n}|;}&\end{array}
$$  

(4) If  $\underline{{\boldsymbol{\mathrm{y}}}}\ne0$   and  $\underline{{\mathbf{X}}}\neq0$   then the range of    $\left|\underline{{\mathbf{y}}}\right\rangle\left\langle\underline{{\mathbf{x}}}\right|$   is the one-dimensional subspace  $\{\bar{\lambda_{\underline{{\mathbf{y}}}}}\mid\lambda\in C\}$  .  

(5)    $\|{\underline{{\mathbf{y}}}}\rangle\langle{\underline{{\mathbf{x}}}}|\|=\|{\underline{{\mathbf{y}}}}\|\|{\underline{{\mathbf{x}}}}\|.$  .  

(6) For any bounded linear operator    $\mathbf{T}$  ,  

$$
\begin{array}{r}{\mathbf{T}|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{x}}}|=|\mathbf{T}\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{x}}}|,}\\ {|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{x}}}|\mathbf{T}=|\underline{{\mathbf{y}}}\rangle\langle\mathbf{T}_{\underline{{\mathbf{x}}}}^{*}|.}\end{array}
$$  

(7) An operator is a projection with dim  $R({\bf T})=1$  , that is the dimensionality of the  range  of  $\mathbf{T}$   is one, if and only if  $\mathbf{T}=\left|\underline{{\mathbf{X}}}\right\rangle\left\langle\underline{{\mathbf{X}}}\right|$   for some unit vector x. In such a case  $R(\mathbf{T})=\{\lambda_{\underline{{\mathbf{X}}}}|\lambda\in\mathbf{C}\}$  .  

(8) If  $\mathbf{P}$   is a projection and    $\{\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2},\,.\,.\,.\,,\underline{{\mathbf{e}}}_{n}\}$   is any orthonormal basis for the subspace  $R({\bf P})$  , then  

$$
\mathbf{P}=\sum_{i=1}^{n}\left|\underline{{\mathbf{e}}}_{i}\right\rangle\left\langle\underline{{\mathbf{e}}}_{i}\right|
$$  

if    $R({\bf P})={\bf H}$   and   $\mathrm{dim}(\mathbf{H})=n$  , then  

$$
\mathbf{P}=\sum_{i=1}^{n}|\underline{{\mathbf{e}}}_{i}\rangle\langle\underline{{\mathbf{e}}}_{i}|=\mathbf{I}.
$$  

(This is the so-called  resolution of unity , or the  completeness property .) The Dirac notation for the inner product   $(\varphi,\mathbf{A}\psi)$   in the previous chapter can  

be written as    $\langle\varphi|\mathbf{A}|\psi\rangle$  . Using the completeness property we can derive some useful identities.  

$$
\begin{array}{c}{{\underline{{\mathtt{x}}}=\mathbf{I\underline{{x}}}\left(\displaystyle\sum_{i=1}^{n}|\underline{{\mathtt{e}}}_{i}\rangle\langle\underline{{\mathtt{e}}}_{i}|\right)\underline{{\mathtt{x}}}=|\underline{{\mathtt{e}}}_{i}\rangle\langle\underline{{\mathtt{e}}}_{i}|\underline{{\mathtt{x}}}+|\underline{{\mathtt{e}}}_{2}\rangle\langle\underline{{\mathtt{e}}}_{2}|\underline{{\mathtt{x}}}+\cdot\cdot\cdot+|\underline{{\mathtt{e}}}_{n}\rangle\langle\underline{{\mathtt{e}}}_{n}|\underline{{\mathtt{x}}}}}\\ {=\displaystyle\sum_{i=1}^{n}\langle\underline{{\mathtt{e}}}_{i}\,|\,\underline{{\mathtt{x}}}\rangle\underline{{\mathtt{e}}}_{i}.}}\end{array}
$$  

In a  real  Hilbert spa    $\langle\underline{{\mathbf{e}}}_{i}\mid\underline{{\mathbf{X}}}\rangle$  is of c  $||\underline{{\mathbf{e}}}_{i}||\mathbf{\nabla}||\underline{{\mathbf{x}}}||$   $\theta$  , w ere    $\theta$   is the angle between the vectors x and e  $\underline{{\mathbf{e}}}_{i}$  , and if  ||  $||\underline{{\mathbf{e}}}_{i}||=1$  || =  1 then  ||  $||\underline{{\mathbf{x}}}||$  ||  cos  θ  is the size of the projection of  $\underline{{\mathbf{X}}}$   onto  $\underline{{\mathbf{e}}}_{i}$  .  

Another useful identity is  

$$
\langle{\underline{{\mathbf{x}}}}\mid{\underline{{\mathbf{y}}}}\rangle=\langle{\underline{{\mathbf{x}}}}\mid\mathbf{I}\mid{\underline{{\mathbf{y}}}}\rangle=\left\langle{\underline{{\mathbf{x}}}}\left|\sum_{i=1}^{n}|{\underline{{\mathbf{e}}}}_{i}\rangle\langle{\underline{{\mathbf{e}}}}_{i}|\right|{\underline{{\mathbf{y}}}}\right\rangle=\sum_{i=1}^{n}\langle{\underline{{\mathbf{x}}}}\mid{\underline{{\mathbf{e}}}}_{i}\rangle\langle{\underline{{\mathbf{e}}}}_{i}|{\underline{{\mathbf{y}}}}\rangle.
$$  

This is familiar because in a real Hilbert space, if  $\underline{{\mathbf{x}}}=(x_{1},\,x_{2},\,.\,.\,.\,.\,,\,x_{n})^{\mathrm{T}}$    and  $\underline{{\mathbf{y}}}=(y_{1},y_{2},.\,.\,.\,,y_{n})^{\mathrm{T}}$    then    $\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{e}}}_{i}\rangle=x_{i}$   and    $\langle\underline{{\mathbf{e}}}_{i}\mid\underline{{\mathbf{y}}}\rangle=y_{i}$   and so  

$$
\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{y}}}\rangle=\sum_{i=1}^{n}x_{i}\,y_{i}\,,
$$  

a well-known form by now.  

The matrix elements of an operator    $\mathbf{A}$   w.r.t. a basis    $\{\underline{{\mathbf{e}}}_{1},\,\underline{{\mathbf{e}}}_{2},\,.\,.\,.\,\,,\,\underline{{\mathbf{e}}}_{n}\}$   are given by    $\langle{\underline{{\mathbf{e}}}}_{i}|\mathbf{A}|{\underline{{\mathbf{e}}}}_{j}\rangle=a_{i j}$  , where    $a_{i j}$   is the matrix element in the  i th row and  j th column. Keeping this interpretation in mind, there are the following identities.  

$$
\langle\underline{{\mathfrak{e}}}_{j}|\mathbf{A}|\underline{{\mathfrak{x}}}\rangle=\langle\underline{{\mathfrak{e}}}_{j}|\mathbf{A}\mathbf{I}|\underline{{\mathfrak{x}}}\rangle=\langle\underline{{\mathfrak{e}}}_{j}|\mathbf{A}\sum_{i=1}^{n}|\underline{{\mathfrak{e}}}_{i}\rangle\langle\underline{{\mathfrak{e}}}_{i}|\underline{{\mathfrak{x}}}\rangle=\sum_{i=1}^{n}\langle\underline{{\mathfrak{e}}}_{j}|\mathbf{A}|\underline{{\mathfrak{e}}}_{i}\rangle\langle\underline{{\mathfrak{e}}}_{i}|\underline{{\mathfrak{x}}}\rangle.
$$  

Another identity reﬂecting the process of applying a matrix (operator) to a vector is  

$$
\mathbf{A}\underline{{\underline{{\sf e}}}}_{k}=\mathbf{I}\mathbf{A}\underline{{\underline{{\sf e}}}}_{k}=\sum_{i=1}^{n}|\underline{{\underline{{\sf e}}}}_{i}\rangle\langle\underline{{\underline{{e}}}}_{i}|\mathbf{A}\underline{{\underline{{e}}}}_{k}=\sum_{i=1}^{n}\langle\underline{{\underline{{e}}}}_{i}|\mathbf{A}|\underline{{\underline{{e}}}}_{k}\rangle\underline{{\underline{{e}}}}_{i}.
$$  

If the  $\underline{{\mathbf{e}}}_{i}$   are the canonical basis and the  ik th element of    $\mathbf{A}$   is    $\langle\underline{{\mathbf{e}}}_{i}|\mathbf{A}|\underline{{\mathbf{e}}}_{k}\rangle$  , then in matrix notation we have  

$$
\mathbf{A}\underline{{\sf e}}_{k}=\left(\begin{array}{c c c c c}{\langle\underline{{\sf e}}_{1}|\mathbf{A}|\underline{{\sf e}}_{1}\rangle}&{.}&{.}&{.}&{\langle\underline{{\sf e}}_{1}|\mathbf{A}|\underline{{\sf e}}_{n}\rangle}\\ {.}&{.}&{.}&{.}&{.}\\ {.}&{.}&{.}&{.}&{.}\\ {.}&{.}&{.}&{.}&{.}\\ {\langle\underline{{\sf e}}_{n}|\mathbf{A}|\underline{{\sf e}}_{1}\rangle}&{.}&{.}&{.}&{\langle\underline{{\sf e}}_{n}|\mathbf{A}|\underline{{\sf e}}_{n}\rangle}\end{array}\right)\left(\begin{array}{c}{0}\\ {.}\\ {1}\\ {.}\\ {0}\end{array}\right)
$$  

$$
\begin{array}{r l}&{=\left(\begin{array}{c c c c}{a_{11}}&{.}&{.}&{.}&{a_{1n}}\\ {.}&{.}&{.}&{.}&{.}\\ {.}&{.}&{.}&{.}&{.}\\ {.}&{.}&{.}&{.}&{.}\\ {a_{n1}}&{.}&{.}&{.}&{a_{n n}}\end{array}\right)\left(\begin{array}{c}{0}\\ {.}\\ {1}\\ {.}\\ {0}\end{array}\right)}\\ &{=\left(\begin{array}{c}{a_{1k}}\\ {.}\\ {.}\\ {a_{n k}}\end{array}\right).}\end{array}
$$  

$\mathrm{I}_{4}$   is a very compact way of describing this calculation. Of course the  $\underline{{\mathbf{e}}}_{i}$   need not be the canonical basis.  

A ﬁnal identity, showing a compact form of matrix multiplication, is  $\langle\underline{{\mathbf{e}}}_{j}\vert\mathbf{AB}\vert\underline{{\mathbf{e}}}_{k}\rangle=$   the  jk th element of  AB ,  

$$
\langle\underline{{\mathbf{e}}}_{j}|\mathbf{A}\mathbf{I}\mathbf{B}|\underline{{\mathbf{e}}}_{k}\rangle=\langle\underline{{\mathbf{e}}}_{j}|\mathbf{A}\sum_{i=1}^{n}|\underline{{\mathbf{e}}}_{i}\rangle\langle\underline{{\mathbf{e}}}_{i}|\mathbf{B}|\underline{{\mathbf{e}}}_{k}\rangle=\sum_{i=1}^{n}\langle\underline{{\mathbf{e}}}_{j}|\mathbf{A}|\underline{{\mathbf{e}}}_{i}\rangle\langle\underline{{\mathbf{e}}}_{i}|\mathbf{B}|\underline{{\mathbf{e}}}_{k}\rangle,
$$  

which is the product rule for multiplying matrices once again in a very compact form. Observe how effectively the resolution of identity is used.  

Earlier on we gave the properties of the outer product of two vectors, or dyad as it is sometimes called. Dirac (1958) has a neat way of introducing this product (see his book on p. 25). Given the identities above we can now express any linear operator as a linear combination of simple dyads.  

$$
\begin{array}{l}{{\displaystyle{\bf A}={\bf I}{\bf A}{\bf I}}}\\ {{\displaystyle\quad=\sum_{i j}\vert\underline{{\mathfrak{e}}}_{i}\rangle\langle\underline{{\mathfrak{e}}}_{i}\vert{\bf A}\vert\underline{{\mathfrak{e}}}_{j}\rangle\langle\underline{{\mathfrak{e}}}_{j}\vert}}\\ {{\displaystyle\quad=\sum_{i j}\langle\underline{{\mathfrak{e}}}_{i}\vert{\bf A}\vert\underline{{\mathfrak{e}}}_{j}\rangle\vert\underline{{\mathfrak{e}}}_{i}\rangle\langle\underline{{\mathfrak{e}}}_{j}\vert}}\\ {{\displaystyle\quad=\sum_{i j}a_{i j}\vert\underline{{\mathfrak{e}}}_{i}\rangle\langle\underline{{\mathfrak{e}}}_{j}\vert,\mathrm{~where~}\langle\underline{{\mathfrak{e}}}_{i}\vert{\bf A}\vert\underline{{\mathfrak{e}}}_{j}\rangle=a_{i j}.}}\end{array}
$$  

An alternative derivation may be found in Nielsen and Chuang (2000) on page 67.  

One additional simple, and important, result that is beautiful to express in this notation is the famous Cauchy–Schwarz inequality, namely  

$$
\begin{array}{r l}&{\quad\quad|\langle\underline{{\mathbf x}}\,|\,\underline{{\mathbf y}}\rangle|^{2}\leq\langle\underline{{\mathbf x}}\,|\,\underline{{\mathbf x}}\rangle\langle\underline{{\mathbf y}}\,|\,\underline{{\mathbf y}}\rangle,\,\mathrm{or}}\\ &{\quad\quad\frac{|\langle\underline{{\mathbf x}}\,|\,\underline{{\mathbf y}}\rangle|^{2}}{\langle\underline{{\mathbf x}}\,|\,\underline{{\mathbf x}}\rangle\langle\underline{{\mathbf y}}\,|\,\underline{{\mathbf y}}\rangle}\leq1,\mathrm{or}}\end{array}
$$  

$$
{\frac{|\left\langle\underline{{\mathbf{x}}}\mid\underline{{\mathbf{y}}}\right\rangle|^{2}}{\|\underline{{\mathbf{x}}}\|^{2}\|\underline{{\mathbf{y}}}\|^{2}}}\leq1.
$$  

To prove this result using the D-notation proceed as follows. Construct an orthonormal basis for the space such that    $\vert\underline{{\mathbf{y}}}\rangle/(\langle\underline{{\mathbf{y}}}\,\vert\,\underline{{\mathbf{y}}}\rangle)^{1}\!\!\!/_{2}$   is the ﬁrst basis vector.  

$$
\begin{array}{r l}&{\langle\underline{{\mathtt{x}}}\mid\underline{{\mathtt{x}}}\rangle\langle\underline{{\mathtt{y}}}\mid\underline{{\mathtt{y}}}\rangle}\\ &{\quad=\displaystyle\sum_{i=1}^{n}\langle\underline{{\mathtt{x}}}\mid\underline{{\mathtt{e}}}_{i}\rangle\langle\underline{{\mathtt{e}}}_{i}\mid\underline{{\mathtt{x}}}\rangle\langle\underline{{\mathtt{y}}}\mid\underline{{\mathtt{y}}}\rangle}\\ &{\quad\ge\displaystyle\frac{\langle\underline{{\mathtt{x}}}\mid\underline{{\mathtt{y}}}\rangle\langle\underline{{\mathtt{y}}}\mid\underline{{\mathtt{x}}}\rangle}{\langle\underline{{\mathtt{y}}}\mid\underline{{\mathtt{y}}}\rangle}\langle\underline{{\mathtt{y}}}\mid\underline{{\mathtt{y}}}\rangle,\mathrm{\,subs}}\\ &{\quad=\langle\underline{{\mathtt{x}}}\mid\underline{{\mathtt{y}}}\rangle\langle\underline{{\mathtt{y}}}\mid\underline{{\mathtt{x}}}\rangle}\\ &{\quad=|\langle\underline{{\mathtt{x}}}\mid\underline{{\mathtt{y}}}\rangle|^{2}.}\end{array}
$$  

This calculation demonstrates nicely the power of the D-notation. Readers hav- ing difﬁculty following this derivation are advised to read Appendix I where the derivation is repeated at the end of the crash course on linear algebra.  

# The trace  

The  trace  of an operator is also referred by some authors as pre-probability Grifﬁths (2002). There are many ways of introducing it, but since we shall largely be interested in in one kind of trace, the trace of a positive self-adjoint operator, the simplest way is to deﬁne it formally and list some of its properties

 (see also Petz and Zem´ anek, 1988).  

The quantity    $\textstyle\sum_{j=1}^{n}\langle{\underline{{\mathbf{e}}}}_{j}|\mathbf{T}|{\underline{{\mathbf{e}}}}_{j}\rangle$  , summed over the vectors in the basis, for any =

  $\mathbf{T}$   is known as the trace of  T . It is independent of the choice of basis and equal to the sum of the diagonal elements of the matrix w.r.t. any orthonormal basis. The mapping  $\mathbf{T}\to\operatorname{tr}(\mathbf{T})$   has the following important properties (Parthasarathy, 1992):  

(1)  $\mathrm{tr}(\alpha\mathbf{T}_{1}+\beta\mathbf{T}_{2})=\alpha\mathrm{tr}(\mathbf{T}_{1})+\beta\mathrm{tr}(\mathbf{T}_{2})

$  (2) tr(  $\operatorname{tr}(\mathbf{T}_{1}\,\mathbf{T}_{2})=\operatorname{tr}(\mathbf{T}_{2}\,\mathbf{T}_{1})$   = ), in fact tr(  $\mathrm{tr}({\bf T}_{1}\,{\bf T}_{2}\;.\;.\;.\;{\bf T}_{k})=\mathrm{tr}({\bf T}_{2}\;.\;.\;.\;{\bf T}_{k}\;{\bf T}_{1})$   = ). A cyclic permutation of the product of operators in the argument of tr does not change the result.

 (3)   $\operatorname{tr}(\mathbf{T})=$   the sum of the eigenvalues of  $\mathbf{T}$   inclusive of multiplicity.

 (4)   $\operatorname{tr}(\mathbf{T}^{*})={\overline{{\operatorname{tr}(\mathbf{T})}}}$  , the trace of the adjoint is the complex conjugate of the trace of  $\mathbf{T}$  .

 (5)   $\operatorname{tr}(\mathbf{T})\geq0$   whenever  $\mathbf{T}\geq0$   (i.e. positive deﬁnite).  

(6) The space of bounded linear operators    $B(\mathbf{H})$   with the inner product  $\langle\mathbf{T}_{1},\,\mathbf{T}_{2}\rangle=\operatorname{tr}(\mathbf{T}_{1}\,\mathbf{T}_{2})$   is a Hilbert space of dimension    $n^{2}$    (see Nielsen and Chuang, 2000, p. 76).  

(7) If    $\lambda\colon B(\mathbf{H})\to C$   is a linear map such that    $\lambda([\mathbf{X},\,\mathbf{Y}])=0$   for all    $\mathbf{X}$  ,  $\mathbf{Y}\in$   $B(\mathbf{H})$  , 4   and  $\lambda(\mathrm{I})=n$  , then    $\lambda(\mathbf{X})=\operatorname{tr}(\mathbf{X})$   for all  X .  

We can immediately derive some simple and important results about the traces of special operators.  

The trace of a projection operator is equal to the dimension of the subspace projected on. Suppose we have  $\mathbf{P}=\mathbf{E}_{1}+\mathbf{E}_{2}+\cdot\cdot\cdot+\mathbf{E}_{k}$  , a projection onto a  $k$  - dimensional subsp e, and    $\mathbf{E}_{i}=\left|\underline{{\mathbf{x}}}_{i}\right\rangle\left\langle\underline{{\mathbf{x}}}_{i}\right|$  , the projector onto the 1-dimensional ray represented by x  $\underline{{\mathbf{X}}}_{i}$  , and the x  $\underline{{\mathbf{X}}}_{i}$   are orthonormal. Then  

$$
\begin{array}{l}{{\mathrm{tr}({\bf P})=\displaystyle\sum_{i=1}^{n}\langle\underline{{\sf e}}_{i}|{\bf P}|\underline{{\sf e}}_{i}\rangle,~\mathrm{letting}~\underline{{\sf e}}_{i}=\underline{{\sf x}}_{i}~~1\leq i\leq k\leq n}}\\ {{\quad\quad\quad=\langle\underline{{\sf e}}_{1}\,|\,\underline{{\sf e}}_{1}\rangle\langle\underline{{\sf e}}_{1}\,|\,\underline{{\sf e}}_{1}\rangle+\cdot\cdot\cdot+\langle\underline{{\sf e}}_{k}\,|\,\underline{{\sf e}}_{k}\rangle\langle\underline{{\sf e}}_{k}\,|\,\underline{{e}}_{k}\rangle+0+\cdot\cdot\cdot+0=k.}}\end{array}
$$  

In particular   $\mathrm{tr}(|\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{x}}}|)=1$  , when  $||\underline{{\mathbf{x}}}||=1$  . A second important result is (Penrose, 1994, p. 318),  

$$
\mathrm{tr}(|\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{y}}}|)=\langle\underline{{\mathbf{y}}}\,|\,\underline{{\mathbf{x}}}.\rangle
$$  

This is easily proved  

$$
\begin{array}{r l r}&{}&{\mathrm{tr(|\underline{{y}}\rangle\langle\underline{{x}}|)}=\displaystyle\sum_{i=1}^{n}\langle\underline{{\sf e}}_{i}\mid\underline{{x}}\rangle\langle\underline{{\sf y}}\mid\underline{{\sf e}}_{i}\rangle}\\ &{}&{=\displaystyle\sum_{i=1}^{n}\langle\underline{{\sf y}}\mid\underline{{\sf e}}_{i}\rangle\langle\underline{{\sf e}}_{i}\mid\underline{{x}}\rangle}\\ &{}&{=\displaystyle\langle\underline{{\sf y}}\mid\sum_{i=1}^{n}|\underline{{\sf e}}_{i}\rangle\langle\underline{{\sf e}}_{i}\parallel\underline{{x}}\rangle}\\ &{}&{=\displaystyle\langle\underline{{\sf y}}|\mathbb{I}\rangle=\langle\underline{{\sf y}}\mid\underline{{\sf x}}\rangle.}\end{array}
$$  

# Density operators  

Our aim in this chapter is to connect probabilities with the geometry of the space. We have already alluded to this previously, where we pointed forward to a famous theorem of Gleason (1957). There are many ways of stating this theorem (Hughes, 1989, Jordan, 1969, Parthasarathy, 1992), but anticipating the discussion to follow I will give Hughes’ version.  

$$
\mathbf{\mu}^{4}\ [\mathbf{X},\mathbf{Y}]=(\mathbf{X}\mathbf{Y}-\mathbf{Y}\mathbf{X}).
$$  

# Gleason’s Theorem  

Let    $\mu$   be any measure on the closed subspaces of a separable (real or complex) Hilbert space  $\mathbf{H}$   of dimension at least 3. There exists a positive self-adjoint operator  $\mathbf{T}$   of trace class such that, for all closed subspaces    $L$   of    $\mathbf{H}$   we have  $\mu(L)=\operatorname{tr}(\mathbf{T}\mathbf{P}_{L})$  .  

In this theorem    $\mathbf{P}_{L}$   is the projection onto    $L$  , and an operator    $\mathbf{T}$   is of  trace class  provided    $\mathbf{T}$   is positive and its trace is ﬁnite. We are interested in measures

  $\mu$   that are probability measures, that is    $\mu(\mathbf{H})=1$  , in which case   $\begin{array}{r l r}{\mathrm{tr}({\bf T}{\bf P}_{H})}&{{}\!\!\!\!=}&{}\end{array}

$   $\operatorname{tr}(\mathbf{T}\mathbf{I})=\operatorname{tr}(\mathbf{T})=1.$  . In the special case where trace class operators are of trace one, they are called  density operators  (or  density matrices ).  

# Deﬁnition  

$\mathbf{D}$   is said to be a density operator if  $\mathbf{D}$   is a trace class operator and  $\operatorname{tr}(\mathbf{D})=1$  .  

Density operators are identiﬁed with  states . A state can be either  pure , in which case the density operator is a projection onto a one-dimensional ray, or it can be a  mixture  of pure states, speciﬁcally, a convex combination of  $k$   pure states, where  $k$   is the rank of the operator (Park, 1967). It is conventional to use the lower case symbol    $\rho$   for the density operator or its equivalent matrix. We will adopt the same convention. There is a large literature on  density opera- tors  scattered throughout the quantum mechanics literature (see Penrose, 1994, Section 6.4), that usually also requires some understanding of the physics; 5   we aim to avoid that and rather link the mathematics directly to the abstract spatial structure.  

Let us recapitulate the situation before applying some of our machinery to IR. We have shown that a state, either pure or mixed, induces a probability measure on the subspaces of a Hilbert space. The algorithm for computing the probability induced by a given state represented by    $\rho$   is    $\mu(L)\!=\!\mathrm{tr}(\rho{\bf P}_{L}).$  . It is easy to check that we have a probability measure by using the properties of trace and deriving the properties listed for such a measure given in Appendix III. There are a number of ways of expressing this probability. For example, when    $\rho$   is a pure state represented by    $|\varphi\rangle\,\langle\varphi|$  ,  

$$
\mathrm{tr}(\rho\mathbf{P}_{L})=\mathrm{tr}(|\varphi\rangle\langle\varphi|\mathbf{P}_{L})=\langle\varphi|\mathbf{P}_{L}|\varphi\rangle=\langle\mathbf{P}_{L}\varphi|\mathbf{P}_{L}\varphi\rangle=||\mathbf{P}_{L}\varphi||^{2},
$$  

or, if  $\rho=\lambda_{1}|\varphi_{1}\rangle\langle\varphi_{1}|+\cdot\cdot\cdot+\lambda_{n}|\varphi_{n}\rangle\langle\varphi_{n}|$  ,  where  $\textstyle\sum\lambda_{i}=1$  , a mixture, then  

$$
\begin{array}{r l}&{\mathrm{tr}(\rho\mathbf{P}_{L})\mathbf{\Phi}=\mathrm{tr}([\lambda_{1}\vert\varphi_{1}\rangle\langle\varphi_{1}\vert+\cdot\cdot\cdot+\lambda_{n}\vert\varphi_{n}\rangle\langle\varphi_{n}\vert]\mathbf{P}_{L})}\\ &{\mathbf{\Phi}=\lambda_{1}\langle\varphi_{1}\vert\mathbf{P}_{L}\vert\varphi_{1}\rangle+\cdot\cdot\cdot+\lambda_{n}\langle\varphi_{n}\vert\mathbf{P}_{L}\vert\varphi_{n}\rangle.}\end{array}
$$  

5  An excellent introduction is Blum (1981), especially Chapter 2.  

Or, if    $\mathbf{P}_{L}=\mathbf{E}_{1}+\mathbf{E}_{2}+\cdot\cdot\cdot+\mathbf{E}_{k}$  , a projector onto a    $k$  -dimensional subspace, then  

$$
\begin{array}{r}{\mathrm{tr}(\rho\mathbf{P}_{L})=\mathrm{tr}(\rho\mathbf{E}_{1}+\cdot\cdot\cdot+\rho\mathbf{E}_{k})\quad\quad}\\ {=\mathrm{tr}(\rho\mathbf{E}_{1})+\cdot\cdot\cdot+\mathrm{tr}(\rho\mathbf{E}_{k}).}\end{array}
$$  

Remember that any Hermit ian matrix A can be expressed as a linear combination of projectors  $\mathbf{A}=\lambda_{1}\mathbf{P}_{1}+\cdot\cdot\cdot+\lambda_{n}\mathbf{P}_{n}$  , where we will assume that the  $\lambda_{i}$   are all different. It is a simple technical issue to deal with the situation when they are not. If we now calculate  

$$
\mathrm{tr}(\rho{\bf A})=\lambda_{1}\mathrm{tr}(\rho{\bf P}_{1})+\cdot\cdot\cdot+\lambda_{n}\mathrm{tr}(\rho{\bf P}_{n}),
$$  

then each   $\operatorname{tr}(\rho\mathbf{P}_{i})$   can be interpreted as the probability of obtaining the real value    $\lambda_{i}$   when we observe  A  (Hermitian) in state    $\rho$  . With this interpretation it is possible to interpret   $\operatorname{tr}(\rho\mathbf{A})$   as an expectation, that is,  

$$
\langle\mathbf{A}\rangle=\operatorname{tr}(\rho\mathbf{A}).
$$  

It is simply a matter of multiplying each possible observed value by its respective probability and then summing them to obtain the expectation.  

This expectation has the usual properties:  

(1)    $\langle c\mathbf{A}\rangle=c\langle\mathbf{A}\rangle$  , where  $c$   is a constant;

 (2)    $\langle\mathbf{A}+\mathbf{B}\rangle=\langle\mathbf{A}\rangle+\langle\mathbf{B}\rangle$  ;

 (3)  $\langle{\bf{I}}\rangle=\!$  .  

In Jordan (1969) the reader will ﬁnd a uniqueness theorem for the algorithm for    $\langle\mathbf{A}\rangle$  .  

# Theorem  

If a ﬁnite expectation value    $\langle\mathbf{A}\rangle$  with properties (1), (2), (3) and some further technical ones, is deﬁned for all bounded operators    $\mathbf{A}$  , then there is a unique density matrix    $\rho$   such that    $\langle\mathbf{A}\rangle=\operatorname{tr}(\rho\mathbf{A})$  .  

Notice also that the expectation value of a projector operator  $\mathbf{P}_{L}$   is the prob- ability measure of the subspace  $L$   projected onto by    $\mathbf{P}_{L}$  .  

# Interpreting tr(.)  

We are now in a position to interpret this mathematical machinery for IR in various ways. The interpretation is mainly geometrical and will establish a crucial link between geometry and probability in vector spaces.  

In information retrieval we often represent a document by a vector   $\underline{{\mathbf{X}}}$  in an  $n$  -dimensional space, and a query by y. Similarity matching is accomplished by computing    $\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{y}}}\rangle$  , usually assuming that    $||\underline{{\mathbf{x}}}||=1=||\underline{{\mathbf{y}}}||$  . Let us say that we are interested in the similarity between a ﬁxed query y and any document x in the space. With our new machinery we can express the fact that the state    $\rho=$   $\lvert\underline{{\mathbf{y}}}\rangle\,\langle\underline{{\mathbf{y}}}\rvert$   induces a probability measure on the subspaces of    $\mathbf{H}$  , and in particular on the 1-dimensional subspaces, namely vectors. Thus we attach a probability to each document vector x via the algorithm:  

$$
\begin{array}{r l}&{\operatorname{tr}(\rho P_{\underline{{\mathbf x}}})=\operatorname{tr}(|\underline{{\mathbf y}}\rangle\langle\underline{{\mathbf y}}|\underline{{\mathbf x}}\rangle\langle\underline{{\mathbf x}}|)}\\ &{\qquad\qquad=\langle\underline{{\mathbf y}}\,|\,\underline{{\mathbf x}}\rangle\operatorname{tr}(|\underline{{\mathbf y}}\rangle\langle\underline{{\mathbf x}}|)}\\ &{\qquad\qquad=\langle\underline{{\mathbf y}}\,|\,\underline{{\mathbf x}}\rangle\langle\underline{{\mathbf x}}\,|\,\underline{{\mathbf y}}\rangle}\\ &{\qquad\qquad=\langle\underline{{\mathbf y}}\,|\,\underline{{\mathbf x}}\rangle\langle\underline{{\mathbf y}}\,|\,\underline{{\mathbf x}}\rangle}\\ &{\qquad\qquad=|\langle\underline{{\mathbf y}}\,|\,\underline{{\mathbf x}}\rangle|^{2}.}\end{array}
$$  

If the Hilbert space is a  real  Hilbert space and    $||\underline{{\mathbf{x}}}||=1=||\underline{{\mathbf{y}}}||$  , then    $\langle\underline{{\mathbf{x}}}|\underline{{\mathbf{y}}}\rangle=$   $\|{\underline{{\mathbf{x}}}}\|{\underline{{\mathbf{y}}}}\|\cos\theta=\cos\theta$   $\operatorname{tr}(\rho P_{\underline{{\mathrm{x}}}})=\cos^{2}\theta$  , thus we end up with the square of the cosine correlation, but interpretable as a probability. So, the query has induced a probability on each document equal to the square of the cosine of the angle between the document and the query. Referring back to Gleason’s Theorem, the density operator corresponding to the query may be a linear combination of a number of 1-dimensional projectors. And, the subspace  $L$   can be of a dimension greater than one.  

It should be clear by now that    $\rho$  , the density operator, can represent a 1- dimensional vector, or a set of vectors, albeit a convex combination of vectors, a fact that will be exploited when we apply the theory to several examples in IR. In most applications in IR we compute a similarity to a given query and a single vector or a set of vectors. For example, when the set of interest is a cluster we compute a similarity between it, via a cluster representative, and a query. Traditionally, a cluster of documents is represented by a vector which in some (usually precise) sense summarises the documents in the cluster

 (Van Rijsbergen, 1979a). So, for example, if a cluster contains  $n$   documents

  $\{{\underline{{\mathbf{d}}}}_{1},.\.\.\,,{\underline{{\mathbf{d}}}}_{n}\}$  , then some average vector of these  $n$   vectors must be calculated.  

More usefully, we calculate a weighted average of the vectors. The same can be achieved by a convex mixture of vectors represented as a mixture of projectors:  

$$
\rho=\lambda_{1}|\underline{{\mathsf{d}}}_{1}\rangle\langle\underline{{\mathsf{d}}}_{1}|+\cdot\cdot\cdot+\lambda_{n}|\underline{{\mathsf{d}}}_{n}\rangle\langle\underline{{\mathsf{d}}}_{n}|,\,\mathrm{where}\,\sum\lambda_{\mathrm{i}}=1.
$$  

The  $\lambda_{i}$   are chosen to reﬂect the relative importance of each vector in the mixture. Although the   ${\underline{{\mathbf{d}}}}_{i}$   do not have to be eigenvectors of    $\rho$  , it can be arranged so that they are, which is accomplished by ﬁnding the orthonormal basis for the subspace spanned by    $\{\underline{{\mathrm{d}}}_{1},\,.\,.\,.\,.\,\,,\,\underline{{\mathrm{d}}}_{n}\}$  . So without loss of generality we can assume that the  ${\underline{{\mathbf{d}}}}_{i}$   form an orthonormal set. If the query is   ${\underline{{\mathbf{q}}}}\left(\|{\underline{{\mathbf{q}}}}\|=1\right)$  ) then a probabilistic matching function is naturally given by  

$$
\begin{array}{r l}&{\mathrm{tr}(\rho|\underline{{\sf q}}\rangle\langle\underline{{\sf q}}|)=\mathrm{tr}(\lambda_{1}|\underline{{\sf d}}_{1}\rangle\langle\underline{{\sf d}}_{1}|+\dots+\lambda_{n}|\underline{{\sf d}}_{n}\rangle\langle\underline{{\sf d}}_{n}|)|\underline{{\sf q}}\rangle\langle\underline{{\sf q}}|}\\ &{\qquad\qquad=\lambda_{1}\mathrm{tr}(|\underline{{\sf d}}_{1}\rangle\langle\underline{{\sf d}}_{1}||\underline{{\sf q}}\rangle\langle\underline{{\sf q}}|)+\dots+\lambda_{n}\mathrm{tr}(|\underline{{\sf d}}_{n}\rangle\langle\underline{{\sf d}}_{n}||\underline{{\sf q}}\rangle\langle\underline{{\sf q}}|)}\\ &{\qquad\qquad=\lambda_{1}\mathrm{tr}(|\underline{{\sf d}}_{1}\rangle\langle\underline{{\sf d}}_{1}|\,|\underline{{\sf d}}_{1}\rangle\langle\underline{{\sf q}}|)+\dots+\lambda_{n}\mathrm{tr}(|\underline{{\sf d}}_{n}\rangle\langle\underline{{\sf d}}_{n}|\,\underline{{\sf d}}_{n}\rangle\langle\underline{{\sf q}}|)}\\ &{\qquad\qquad=\lambda_{1}\cos^{2}\theta_{1}+\dots+\lambda_{n}\cos^{2}\theta_{n},}\end{array}
$$  

where  $\theta_{i}$   was deﬁned earlier as the angle between  ${\underline{{\mathbf{d}}}}_{i}$   and  $\underline{{\boldsymbol{\mathrm{q}}}}$  . The object  $\rho$   can also be interpreted as the centroid of    $\{{\underline{{\mathbf{d}}}}_{1},\dots,{\underline{{\mathbf{d}}}}_{n}\}$  , but, notice that    $\rho$   and    $|\underline{{\mathbf{q}}}\rangle\langle\underline{{\mathbf{q}}}|$  are operators, not vectors. By working in the dual space of operators we have a framework that uniﬁes our vector operations and probabilities.   If we wish to measure the probability matching function between a cluster and a query q, we simply calculate  

$$
\mathrm{tr}(\rho|\underline{{\mathbf{q}}}\rangle\langle\underline{{\mathbf{q}}}|),
$$  

where  $\operatorname{tr}(.)$   is a linear functional on the space of operators. It turns out that one can in fact deﬁne an inner product on that space by   $\operatorname{tr}(\mathbf{A}^{*}\mathbf{B})\equiv\left\langle\mathbf{A}\mid\mathbf{B}\right\rangle$  , where  A and    $\mathbf{B}$   are linear operators, this is known as the Hilbert–Schmidt or trace inner product (Nielsen and Chuang, 2000).  

It is worth commenting on this further level of abstraction. We have inter- preted the trace function for a set of special linear operators, density operators and projectors, as giving a probability. With the deﬁnition of the trace inner product we have something more general, but nevertheless we may ﬁnd it useful to interpret even this special case as an inner product. In IR we are quite familiar with the notion of inner product between objects. In some cases it may be an advantage to view the similarity between a query and, say, a cluster representative as an inner product. The trace inner product formalises this in a neat way.  

# Co-ordination level matching  

One of the oldest matching functions in IR is co-ordination level matching. Basically it counts the number of index terms shared between a query and a document. It is enlightening to translate this matching function into the new notation. So let  

$$
\begin{array}{l}{\underline{{\mathsf{q}}}=(q_{1},\ldots,q_{n}),}\\ {\underline{{\mathsf{x}}}=(x_{1},\ldots,x_{n}),}\end{array}
$$  

and in the ﬁrst instance let them be binary vectors. Geometrically, a vector   $\underline{{\boldsymbol{\mathrm{q}}}}$  matches a vector x in the  i th position when    $\langle\underline{{\mathbf{e}}}_{i}\mid\underline{{\mathbf{q}}}\rangle$  and    $\langle\underline{{\mathbf{e}}}_{i}\mid\underline{{\mathbf{X}}}\rangle$  are both non-zero.  

More generally, to calculate the number of index terms that any two vectors  $\underline{{\mathbf{X}}}$   and y share we express  

$$
\begin{array}{l}{\underline{{\mathbf{x}}}=x_{1}\underline{{\mathbf{e}}}_{1}+\cdot\cdot\cdot+x_{n}\underline{{\mathbf{e}}}_{n},}\\ {\underline{{\mathbf{y}}}=y_{1}\underline{{\mathbf{e}}}_{1}+\cdot\cdot\cdot+y_{n}\underline{{\mathbf{e}}}_{n}.}\end{array}
$$  

If  $x_{i}=1$   or 0 and  $y_{i}=1$   or 0, then  

$$
\begin{array}{l}{{\displaystyle\langle\underline{{{\bf x}}}\,|\,\underline{{{\bf y}}}\rangle=\sum_{i,j}x_{i}y_{j}\langle\underline{{{\bf e}}}_{i}\,|\,\underline{{{\bf e}}}_{j}\rangle,~{\mathsf{b u t}}\,\langle\underline{{{\bf e}}}_{i}\,|\,\underline{{{\bf e}}}_{j}\rangle=\delta_{i j}}}\\ {~~}\\ {{\displaystyle~~=\sum_{i,j}x_{i}y_{j}\delta_{i j}}}\\ {{\displaystyle~~=\sum_{i}x_{i}y_{i}},}\end{array}
$$  

which counts the number of times that  $x_{i}$   and    $y_{i}$   are both 1. The formulation also shows how cosine correlation is a simple generalisation of co-ordination level matching. If  $\underline{{\mathbf{X}}}$   and  $\underline{{\boldsymbol{\mathrm{y}}}}$   are two vectors as before but now every  $x_{i}$   and    $y_{i}$   is either greater than or equal to zero, then  

$$
\begin{array}{c}{{\displaystyle\langle\underline{{{\texttt X}}}\,|\,\underline{{{\texttt y}}}\rangle=\sum_{i}x_{i}y_{i}\,\langle\underline{{{\texttt e}}}_{i}\,|\,\underline{{{\texttt e}}}_{i}\rangle}}\\ {{=\|\underline{{{\texttt x}}}\|\,\|\underline{{{\texttt y}}}\|\cos\varphi}}\\ {{\cos\varphi=\frac{\langle\underline{{{\texttt x}}}\,|\,\underline{{{\texttt y}}}\rangle}{\|\underline{{{\texttt x}}}\|\,\|\underline{{{\texttt y}}}\|},}}\end{array}
$$  

$$
\cos\varphi=\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{y}}}\rangle.
$$  

The reader will have observed that the basis vectors   $\underline{{\mathbf{e}}}_{i}$   have been retained throughout the computation. For the standard basis    $\langle\underline{{\mathbf{e}}}_{i}\,|\,\underline{{\mathbf{e}}}_{j}\rangle=\delta_{i j}$  were to refer x and y to a non-standard basis, that is, assuming that  {  $\{{\underline{{\mathbf{e}}}}_{1},\dots,{\underline{{\mathbf{e}}}}_{n}\}$  } were an arbitrary set of linearly independent vectors spanning the space, then that computation of the inner product referred to such a basis would become  

$$
\langle{\underline{{\mathbf{x}}}}\,|\,{\underline{{\mathbf{y}}}}\rangle=\sum_{i,j}x_{i}g_{i j}y_{j},{\mathrm{where~}}\langle{\underline{{\mathbf{e}}}}_{i}\,|\,{\underline{{\mathbf{e}}}}_{j}\rangle=g_{i j}.
$$  

The matrix    $\mathbf{G}=(g_{i j})$   is called the metric matrix (Sadun, 2001). In matrix terms,  

$$
\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{y}}}\rangle=(x_{1},\dots,x_{n})\mathbf{G}\,\left(\begin{array}{c}{y_{1}}\\ {\cdot}\\ {\cdot}\\ {\cdot}\\ {y_{n}}\end{array}\right)\,.
$$  

For example, in the space  $R^{2}$  , let    $\{(1,0),(1,1)\}$   be the basis, then  

$$
\begin{array}{r l}&{\langle\underline{{\mathsf{e}}}_{1}\,|\,\underline{{\mathsf{e}}}_{1}\rangle=1,}\\ &{\langle\underline{{\mathsf{e}}}_{1}\,|\,\underline{{\mathsf{e}}}_{2}\rangle=1,}\\ &{\langle\underline{{\mathsf{e}}}_{2}\,|\,\underline{{\mathsf{e}}}_{1}\rangle=1,}\\ &{\langle\underline{{\mathsf{e}}}_{2}\,|\,\underline{{\mathsf{e}}}_{2}\rangle=2,}\\ &{\Rightarrow\mathbf{G}=\left(\begin{array}{l l}{1}&{1}\\ {1}&{2}\end{array}\right).}\end{array}
$$  

And so  

$$
\begin{array}{r l}{\underline{{\mathtt{X}}}\!\!=\!\!a_{1}\underline{{\mathtt{b}}}_{1}+a_{2}\underline{{\mathtt{b}}}_{2},}&{}\\ {\underline{{\mathtt{y}}}\!=\!\!c_{1}\underline{{\mathtt{b}}}_{1}+c_{2}\underline{{\mathtt{b}}}_{2}}&{}\\ {\mathrm{and~}\langle\underline{{\mathtt{x}}}\,|\,\underline{{\mathtt{y}}}\rangle=(a_{1}}&{a_{2})\left(\begin{array}{l l}{1}&{1}\\ {1}&{2}\end{array}\right)\binom{c_{1}}{c_{2}}\,.}\end{array}
$$  

This is the inner product calculated with reference to the new basis    $\{\underline{{\mathsf{b}}}_{1},\underline{{\mathsf{b}}}_{2}\}$  .  

In several IR applications, for example, latent semantic indexing, a new basis is constructed, usually consisting of a small set of linearly independent vectors. If we refer our documents and queries to these new basis vectors, then the matrix G , the metric matrix above, allows us to calculate an inner product in a simple way.  

# Pseudo-relevance feedback  

In relevance feedback the user is asked to judge which are the top    $k$   relevant documents in a similarity ranking presented to him or her. In pseudo-relevance feedback it is assumed that the top    $k$   documents in a ranking are relevant. From that one can then derive information to modify the query to reﬂect more accurately the information need of the user. One can illustrate the process geometrically in three dimensions as follows, with a basis    $\{\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2},\underline{{\mathbf{e}}}_{3}\}$  .  

![](images/febf25e89bf505d2a109d61bbc7c56ef07b76ecf80bd40e0fb1207d5845a9f82.jpg)  

Let us say that in this 3-dimensional vector space the query  $\underline{{\boldsymbol{\mathrm{q}}}}$   lies in the 2- dimensional plane given by   $[\underline{{\mathbf{e}}}_{1},\;\underline{{\mathbf{e}}}_{2}]$  . Let  $\underline{{\mathbf{X}}}$   be a typical document, then the probabilistic similarity is given by  

$$
\operatorname{tr}(|{\underline{{\mathbf{q}}}}\rangle\langle{\underline{{\mathbf{q}}}}\mid{\underline{{\mathbf{x}}}}\rangle\langle{\underline{{\mathbf{x}}}}|)=|\langle{\underline{{\mathbf{q}}}}\mid{\underline{{\mathbf{x}}}}\rangle|^{2}=\cos^{2}\theta,\quad{\mathrm{~where~}}\|{\underline{{\mathbf{x}}}}\|=\|{\underline{{\mathbf{q}}}}\|=1.
$$  

The matching value   $\cos^{2}\theta$   can be computed for each document  $\underline{{\mathbf{X}}}.$  , and a rank- ing of    $k$   documents is given by ranking the documents in inverse order of  $\cos^{2}\theta$  . There are essentially two ways of modifying the query in the light of the ranking.  

(1) Rotate  $\underline{{\boldsymbol{\mathrm{q}}}}$   in the plane  $[\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2}]$  .

 (2) Expand  $\underline{{\boldsymbol{\mathrm{q}}}}$   so that it becomes a vector in   $[\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2},\underline{{\mathbf{e}}}_{3}]$  .  

There are many ways of implementing this (Baeza-Yates and Ribeiro-Neto, 1999). For example, if there are a number of documents, one might project each document  $\underline{{\mathbf{X}}}_{i}$   onto the plane   $[\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2}]$  . This is easily expressed in our new notation. The projector  $\mathbf{P}$   onto   $[\underline{{\mathbf{e}}}_{1},\underline{{\mathbf{e}}}_{2}]$   is denoted by  ${\bf P}=|\underline{{{\sf e}}}_{1}\rangle\langle\underline{{{\sf e}}}_{1}|+|\underline{{{\sf e}}}_{2}\rangle\langle\underline{{{\sf e}}}_{2}|$  . To project  $\underline{{\mathbf{X}}}_{i}$  , which itself is  $\mathtt{x}_{i}=\alpha_{i1}\,|\,\underline{{\mathsf{e}}}_{1}\rangle+\alpha_{i2}|\underline{{\mathsf{e}}}_{2}\rangle+\alpha_{i3}|\underline{{\mathsf{e}}}_{3}\rangle$  , simply compute  

$$
\begin{array}{r l}&{(|\underline{{\mathfrak{e}}}_{1}\rangle\langle\underline{{\mathfrak{e}}}_{1}|+|\underline{{\mathfrak{e}}}_{2}\rangle\langle\underline{{\mathfrak{e}}}_{2}|)\underline{{\mathfrak{x}}}_{i}=\langle\underline{{\mathfrak{e}}}_{1}\,|\,\underline{{\mathfrak{x}}}_{i}\rangle\,|\,\underline{{\mathfrak{e}}}_{1}\rangle+\langle\underline{{\mathfrak{e}}}_{2}\,|\,\underline{{\mathfrak{x}}}_{i}\rangle\,|\,\underline{{\mathfrak{e}}}_{2}\rangle}\\ &{\qquad\qquad\qquad\qquad=\alpha_{i1}|\,\underline{{\mathfrak{e}}}_{2}\rangle+\alpha_{i2}|\,\underline{{\mathfrak{e}}}_{2}\rangle}\\ &{\qquad\qquad\qquad\qquad=\underline{{\mathfrak{z}}}_{i}.}\end{array}
$$  

This calculation can be done for any  $\underline{{\mathbf{X}}}_{i}$  . Now we have a bundle of vectors projected from 3-d into 2-d. A modiﬁcation of  $\underline{{\boldsymbol{\mathrm{q}}}}$   might be to transform q into a vector  $\underline{{\boldsymbol{\mathrm{q}}}}^{\prime}$    which lies somewhat closer to the set of projected document vectors. The density operator  $\rho$   representing this set would be a mixture of these vectors, so we take a convex combination of the    $\left|\underline{{\mathbf{Z}}}_{i}\right\rangle\left\langle\underline{{\mathbf{Z}}}_{i}\right|$  , that is  

$$
\rho=\sum_{i=1}^{k}\lambda_{i}\vert\underline{{\mathbf{z}}}_{i}\rangle\langle\underline{{\mathbf{z}}}_{i}\vert.
$$  

The trace,  $\mathbf{tr}(\rho\vert\underline{{\mathbf{q}}}\rangle\langle\underline{{\mathbf{q}}}\vert)$  , gives us the probabilistic similarity between   $\underline{{\boldsymbol{\mathrm{q}}}}$   and the set of    $k$   projected vectors. A typical feedback operation would be to move   $\underline{{\boldsymbol{\mathrm{q}}}}$  closer to the set of  $k$   documents. In two dimensions this can be accomplished by applying a linear transformation to q. A suitable transformation in this context would be a unitary transformation,   which represents a rotation of the vector   $\underline{{\boldsymbol{\mathrm{q}}}}$  through an angle    $\phi$   into   $\underline{{\boldsymbol{\mathrm{q}}}}^{\prime}$    (see Mirsky, Chapter 8, 1990, for details). The extent of the rotation, or the size of angle    $\phi$  , is determined by   $\mathbf{tr}(\rho|\underline{{\mathbf{q}}}\rangle\langle\underline{{\mathbf{q}}}|)$  . The relationship  $\phi\!=\!f\!(\operatorname{tr}(\rho|\underline{{\mathbf{q}}}\rangle\langle\underline{{\mathbf{q}}}|))$   would need to be determined; it could be a simple mapping,  $f\colon[0,1]\rightarrow[0,2\pi]$  , or further heuristic information could be used to constrain or elaborate  $f.$   Here is an illustration:  

$$
\binom{q_{1}^{\prime}}{q_{2}^{\prime}}=\binom{\cos\phi}{\sin\phi}\,\quad-\binom{\sin\phi}{q_{2}}\,.
$$  

The matrix represents a counter-clockwise rotation of  $\underline{{\boldsymbol{\mathrm{q}}}}$   in the plane through  $\phi$  , thus moving q closer to the projections of the documents  $\underline{{\mathbf{X}}}_{i}$  .  

This is a very simple example but it illustrates one aspect of the geometry that may have gone unnoticed. At no stage was the deﬁnition of the inner product made explicit; the choice of it was left open. So, for example, if we had chosen  

$$
\langle\underline{{\mathbf{x}}}\,|\,\underline{{\mathbf{y}}}\rangle=\sum_{i=1}^{n}x_{i}\,y_{i}\,.
$$  

the discussion would have been the same. In our example we chose a unitary matrix that represented a rotation in the plane; in higher dimensions such a nice geometric interpretation may not be available.  

Query expansion is slightly different, but using the unitary transformation above gives us the clue. To transform the query into a 3-d vector we again transform   $\mathbf{q}$   into  $\underline{{\boldsymbol{\mathrm{q}}}}^{\prime}$  , but this time the transformation moves   $\underline{{\boldsymbol{\mathrm{q}}}}$   out of the 2-d plane into 3-d. The process is the same, but  $\rho$   is now represented as a mixture of the original (unprojected) vectors. That is,  

$$
\rho=\sum_{i}\lambda_{i}|_{\underline{{\mathbf{x}}}_{i}}\rangle\langle{\underline{{\mathbf{x}}}}_{i}|,\,\mathrm{where}\,\sum_{i}\lambda_{i}=1
$$  

and   $\mathbf{tr}(\rho|\underline{{\mathbf{q}}}\rangle\langle\underline{{\mathbf{q}}}|)$   again gives us the matching value between the query and the set of    $k$   top ranking documents.  

# Relevance feedback  

The situation with relevance feedback is somewhat different from that with pseudo-relevance feedback. A ranking (or set of documents) is presented to the user and he, or she, is asked to judge them choosing between relevance and non- relevance (for simplicity we will assume that unjudged ones are non-relevant). The relevance decisions are then used to construct a new query incorporating the relevance information. The two best known techniques for doing this, the one based on the probabilistic model and Rocchio’s method, are both examined in Van Rijsbergen (1979a). We will describe the ﬁrst of these only.  

A basic formulation of the probabilistic model for relevance feedback may be summarised as follows. Given a set of retrieved documents we divide it into a set of relevant documents and a set of non-relevant ones. We now look at the frequency of occurrence of index terms in both the relevant and non-relevant sets. Thus for each index term  $i$   we can calculate  $p_{i}$  , the frequency with which    $i$  occurs in the relevant set, and  $q_{i}$  , the frequency with which    $i$   occurs in the non- relevant set. Using these  $p_{i}\mathbf{s}$   and    $q_{i}s$  , there are now various formulations for implementing relevance feedback. In the decision-theoretic version described in Van Rijsbergen (1979a), a function    $g(\underline{{\boldsymbol X}})$   is derived:  

$$
g({\underline{{\mathbf{x}}}})=\sum_{i=1}^{n}x_{i}\log\left[{\frac{p_{i}(1-q_{i})}{q_{i}(1-p_{i})}}\right]+\;{\mathrm{constant}},
$$  

where x is a document on  $n$   index terms with  $x_{i}=1$   or 0 depending on whether the  i th index term is present or absent. Then for each unseen document x the function  $g(\underline{{\boldsymbol X}})$   is evaluated and used either to rank documents, or as a decision function to separate the relevant from the non-relevant. We can safely ignore the constant.  

If we let  

$$
\begin{array}{r l}&{\widetilde{\alpha}_{i}=\log\left[\underline{{p_{i}(1-q_{i})}}\right],}\\ &{g(\underline{{\mathbf{x}}})=\widetilde{\alpha}_{1}x_{1}+\cdot\cdot\cdot+\widetilde{\alpha}_{n}x_{n},}\end{array}
$$  

$\alpha_{i}$   be the rescaled version such that    $\textstyle\sum_{i=1}^{n}\alpha_{i}=1$   =  1 and  $\alpha_{i}\geq0$  , we have a = function not too dissimilar from the one that arises in Gleason’s Theorem. In  $g(\underline{{\boldsymbol X}})$  the varia re binary variables, so that for    $x_{i}=1$  ,  $g(\underline{{\boldsymbol X}})$   is incremented by  $\alpha_{i}$   and for  $x_{i}=0$   0 it is ignored.  

With this intuition let us express    $g(\underline{{\boldsymbol{\mathbf{\rho}}}})$   as an operator to be applied to any unseen document x. For this we write  

$$
\rho=\alpha_{1}|x_{1}\rangle\langle x_{1}|+\cdot\cdot\cdot+\alpha_{n}|x_{n}\rangle\langle x_{n}|,
$$  

where  $\left|x_{i}\right\rangle\left\langle x_{i}\right|$   is the orthogonal projection onto the  i th basis vector 8   representing the  i th index term. Now consider any unseen normalised  $\underline{{\boldsymbol{\mathbf{X}}}}$  . It can be expressed as  ${\underline{{\mathbf{x}}}}=\beta_{1}|x_{1}\rangle+\cdot\cdot\cdot+\beta_{n}|x_{n}\rangle$  , where    $\sum\beta_{i}^{2}=1$    1, and for   $\underline{{\boldsymbol{\mathbf{X}}}}$   a binary vector all the  $\beta_{i}$   are equal. Now apply the operator  ρ  to x to get  

$$
\begin{array}{r l}&{\rho_{\underline{{\mathbf{X}}}}=(\alpha_{1}|\mathbf{x}_{1}\rangle\langle x_{1}|+\cdot\cdot\cdot+\alpha_{n}|x_{n}\rangle\langle x_{n}|)(\beta_{1}|x_{1}\rangle+\cdot\cdot\cdot+\beta_{n}|x_{n}\rangle)}\\ &{\quad=\alpha_{1}\beta_{1}|x_{1}\rangle+\cdot\cdot\cdot+\alpha_{n}\beta_{n}|x_{n}\rangle,}\end{array}
$$  

where  $\alpha_{i}\beta_{i}\geq0$   if  $\beta_{i}\geq0$  . If the index term is missing for   $\underline{{\mathbf{X}}}$   then    $\beta_{i}=0$   and  $\alpha_{i}\beta_{i}=0$  . The expression    $\rho_{\underline{{\mathbf{X}}}}$   contains the same information as  $g(\underline{{\boldsymbol X}})$  . One further step in generalisation is needed. Instead of applying    $\rho$   to  $\underline{{\mathbf{X}}}$   we calculate the trace,  $\mathrm{tr}(\rho_{\underline{{\mathbf{X}}}})=\mathrm{tr}(\rho|\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{x}}}|)$  . This calculation gives us the probability induced by  $\rho$  , which contains the relevance information, on the space of vectors  $\underline{{\mathbf{X}}}$  . Clearly this process can be iterated, each time generating a different density matrix  $\rho$  .  

The density matrix    $\rho$   can be thought of as a generalised query. This query is revised in the light of the relevance feedback from the user, and is applied as an operator to each document to produce a probability value via the trace calculation. These values can then be used to order the documents, after which the process can be repeated with a further algebraic application of the the operator representing the revised query. This process very nicely encapsulates the mathematics of relevance feedback in a simple manner.  

There are a number of attractive things about this formulation that are worth describing.  

Firstly, the particular ‘index terms’ chosen, that is the dimensions    $\left|x_{i}\right\rangle$  span- ning the space do not need to be the index terms in the query. This is especially important when the objects are images. The basis vectors of the space to be projected onto can be determined by ﬁnding, for example, the eigenvectors of the observable representing the query.  

Secondly, there is nothing to prevent the density operator    $\rho$   from being expressed as a convex combination of projectors, each of which projects on an arbitrary subspace. Thus, if there is uncertainty about the relative importance of, say, two index terms  $i$   and  $j$  , then we include a projector onto the subspace spanned by    $\left|x_{i}\right\rangle$  and    $|x_{j}\rangle$  , or the projector    $\left|x_{i}\right\rangle\left\langle x_{i}\right|+\left|x_{j}\right\rangle\left\langle x_{j}\right|$  .  

Thirdly, there is no intrinsic requirement that the basis vectors be orthogonal. Of course they will be so, if they are the eigenvectors of a self-adjoint linear operator.  

Fourthly, the formulation readily extends to inﬁnite dimensional spaces, which may be important when representing image objects.  

Finally, the vectors do not have to be binary.   $\operatorname{tr}(\rho|\underline{{\mathbf{X}}}\rangle\langle\underline{{\mathbf{X}}}|$   works equally well for (normalised) vectors x that are non-binary.  

# Dynamic clustering  

In this section we give an account of the way in which the geometry of the information space presented in the earlier chapters may be applied to one class of IR problems. We have chosen clustering and in particular dynamic clustering. There are several reasons for concentrating on this area: ﬁrst and foremost because the presence or need for a query is not essential. Secondly, because clustering is one of the techniques in IR (although it comes in many ﬂavours) that attempts to exploit seriously the geometry of the information space. And thirdly, because the technique is not overly inﬂuenced by the medium of the objects. For example, text-based objects are often organised into an inverted ﬁle, or Galois connection (see Chapter 2), because of the existence of keywords, but this organisation it not the obvious one to choose for image objects. Instead some other organisation, for example clustering, may be more appropriate.  

Imagine that you, the reader, as a user, are presented with a large collection of objects. Amongst those objects are some that are of interest to you and would, if you could ﬁnd them, satisfy your current information need. In a fantasy world you could step into the information space, look around you, and if you did not like what you found, you could move to a different location to continue searching. If you did like what you found it would undoubtedly inﬂuence where you would look next. Notice that even in this fantasy world we use a spatial metaphor for describing how we are guided to move around it. Also, there is no question of a query, we simply examine objects, and in the light of observations we decide what to do next. To put it in terms of our paradigm, the user makes observations through interaction with objects. The results of these observations inﬂuence the way the information space is viewed from then on.  

We are unable to step literally into an information space, but we can make it appear as if we do. For this we place our objects in an abstract geometric space and give the user access to this space by way of an interface through visualisation or other forms of presentation. We can keep displaying the ever-changing point of view of the user. It is never the space that changes but the perspective or point of view of the user. Pinning this down in information retrieval terms, it is the probability that an object may be found relevant that is altered, depending on what the user has found relevant thus far. This is not a completely new notion; it was alluded to many times in the earlier IR literature, for example, by Goffman, and more recently by Borland.  

. . . that the relevance of the information from one document depends upon what is already known about the subject, and in turn affects the relevance of other documents subsequently examined.  

(Goffman, 1964)  

That is the relevance or irrelevance of a given retrieved document may affect the user’s current state of knowledge resulting in a change of the user’s information need, which may lead to a change of the user’s perception/interpretation of the subsequent retrieved documents . . .  

(Borland, 2000)  

In other words, the probability of relevance is path-dependent: different paths to the same object may lead to different probabilities. Therefore a probability measure on the space varies, or equivalently it is dependent, or conditioned, on the objects that have been judged and the order in which they have been judged.  

All the foregoing pre-supposes that we have some way of moving from object to object by way of a metric on the space. Such a metric is distance-like and usually has the following properties repeated here for convenience.  

$\begin{array}{r l}&{d(x,y)\geq0\;\mathrm{for~all}\;x,y,}\\ &{d(x,x)=0\;\mathrm{for~all}\;x,}\\ &{d(x,y)=d(y,x),}\\ &{d(x,y)\leq d(x,z)+d(z,y),}\\ &{\{d(x,y)\leq\operatorname*{max}\left[d(x,z),d(z,y)\right]\},}\end{array}$  symmetry , triangle inequality , ultrametric inequality .  

The ﬁrst four conditions deﬁne a standard metric, the triangle inequality may be omitted and only the weaker ﬁfth condition holds, thereby deﬁning an ultrametric.  

An abstract Hilbert space comes endowed with a metric structure, although the precise choice, Euclidean or non-Euclidean, is left open. So if we embed our objects in a Hilbert space we are free to choose the metric that is most meaningful from an IR point of view. There is a large literature on the choice of metrics (Harman, 1992), in which the choice is mostly resolved empirically through experimentation.  

The general IR problem can now be stated. Given that the user has seen a number of objects and made decisions regarding their relevance, how can we present to the user, or direct the user to, a number of objects that are  likely  to be relevant. Notice how the word ‘likely’ has crept into the discussion, meaning that we expect unseen objects to vary in their estimated relevance for the user. There are in the IR literature many models that specify exactly how such an estimate may be calculated (Belew, 2000, Van Rijsbergen, 1979a, Salton and McGill, 1983, Dominich, 2001 and Sparck Jones and Willett, 1997), usually starting from a query that represents the information need. We want to leave the idea of the query out of consideration and concentrate on how a set of selected documents 9   can inﬂuence the estimation of relevance.  

The original basis for this way of thinking – retrieval without query – was ﬁrst detailed in Campbell and Van Rijsbergen (1996). It has been assumed that the nearness of a document to another object is evidence of likely co- relevance, an idea that has been expressed as the Cluster Hypothesis (Van Rijsbergen,1979a)andre-expressedseveraltimes(Croft,1978,Voorhees,1985, Hearst and Pedersen, 1996 and Tombros, 2002). Going back to the geometry of the information space enables us to calculate a probability measure reﬂecting relevance in the light of already accepted objects. One possible interpretation of such a measure is that it captures aboutness, which in turn reﬂects relevance.  

Let us illustrate this by a small abstract example. Let’s say that we have accepted    $k$   objects,   namely,  $\mathrm{Y}=\{\underline{{\mathbf{y}}}_{1},.\.\.\,.\,,\underline{{\mathbf{y}}}_{k}\}$   and we wish to estimate the likely relevance of all those objects not in Y. Let  $\underline{{\mathbf{Z}}}$   be one such object, then intuitively we are interested in estimating the extent to which  $\underline{{\mathbf{Z}}}$  is about Y. One way of capturing the extent to which  $\underline{{\mathbf{Z}}}$   is about   $\mathrm{Y}$   is to measure the extent to which  $\mathrm{Y}$   implies  $\underline{{\mathbf{Z}}}$  . This is based on a view of IR as plausible inference 11 and there are many ways in which it can be formalized (Crestani  et al ., 1998). However, the different ways have all been based on the Logical Uncertainty Principle (LUP) initially formulated in Van Rijsbergen (1986), and we will reformulate it here using the geometry of Hilbert space. We will tackle the simple case of a single object   $\mathrm{Y}=\{\underline{{\sf y}}\}=\underline{{\sf y}}$   plausibly implying an object  $\underline{{\mathbf{Z}}}$  .  

Conventionally, these objects are represented by vectors in some space and once again we assume a Hilbert space. LUP requires us to measure the uncertainty of  $\underline{{\boldsymbol{\mathrm{y}}}}\to\underline{{\boldsymbol{\mathrm{z}}}}$   by measuring the amount of extra information that needs to be added to y so that z can be deduced. One way of measuring this information is to measure the size of the orthogonal projection of y onto z, and use 1- (projection) 2   as that measure. In Van Rijsbergen (2000) a formal justiﬁcation of this approach can be found without the use of Hilbert space theory. In the case of a real Hilbert space the projection is given by  

$$
\langle{\underline{{\mathbf{y}}}}\,|\,{\underline{{\mathbf{x}}}}\rangle=\|{\underline{{\mathbf{y}}}}\|\,\|{\underline{{\mathbf{x}}}}\|\cos\theta,
$$  

which has the familiar simple interpretation as the cosine of the angle between the two vectors when they are normalised, that is, when    $\|\underline{{\mathbf{y}}}\|=1$   and    $\|{\underline{{\mathbf{x}}}}\|=1$  . An interpretation motivated by quantum mechanics would lead us to suggest  $1-\cos^{2}\theta$   as the appropriate measure, 13   because we can interpret  $\cos^{2}\theta$   as a probability measure induced by y on the set of all subspaces of   $\mathrm{H}$  , including of course the subspaces corresponding to the 1-dimensional vectors  $\underline{{\mathbf{Z}}}$   (see Amati and Van Rijsbergen, 1998, p. 189–219) for a more general discussion). If the space is complex the probability measure would be given by    $|\langle{\underline{{\mathbf{y}}}}\,|\,{\underline{{\mathbf{z}}}}\rangle|^{2}$  . This example is a very special case. Let us see how to generalise it.  

Although we may assert that   $\underline{{\boldsymbol{\mathrm{y}}}}$   and   $\underline{{\mathbf{Z}}}$   are vectors in a high-dimensional space, in practice they rarely are, as we can be sure of the values of only a small number of components in the vector, all the other components being either undeﬁned or assumed to have some arbitrary value. Therefore, without any further knowledge, one could assume that y and  $\underline{{\mathbf{Z}}}$   are in fact any vectors lying in the corresponding subspaces  $L_{y}$   and  $L_{z}$  . It is at this point that the power of the theory based on Gleason’s Theorem comes into play. It is natural to represent a subspace by a projection operator onto it, that is,  $L_{y}$   is represented by  $\mathbf{P}_{y}$   and  $L_{z}$   is represented by  $\mathbf{P}_{z}$  . If    $L_{y}$   and    $L_{\mathrm{z}}$   are only 1-dimensional subspaces, that is vectors, then  

$$
\begin{array}{r}{\mathbf{P}_{y}=|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}|,}\\ {\mathbf{P}_{z}=|\underline{{\mathbf{z}}}\rangle\langle\underline{{\mathbf{z}}}|}\end{array}
$$  

are the projectors onto the relevant subspaces expressed in the Dirac notation. Returning to the issue of measuring the extra information to be added to y through a probability measure on the space induced by    $\mathbf{P}_{y}$  , we can now deploy Gleason’s Theorem,  

$$
\mu_{y}(L_{z})=\operatorname{tr}(\mathbf{P}_{y}\mathbf{P}_{z}),
$$  

13  See the Prologue and Wootters (1980b).  

which gives us an algorithm for computing the probability measure for any subspace  $L_{z}$   induced by the subspace  $L_{y}$  . We repeat that  

$$
(\mathbf{A},\,\mathbf{B})=\operatorname{tr}(\mathbf{A}^{*}\mathbf{B})
$$  

is a natural inner product on the space of linear operators with dimension  $n^{2}$    if the dimension of    $\mathbf{H}$   is  $n$  . So our probability    $\mu_{y}(L_{z})$   is the inner product between  $\mathbf{P}_{y}$   and  $\mathbf{P}_{z}$  .  

A sanity check shows that if    $\mathbf{P}_{y}=|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}|$   and    $\mathbf{P}_{z}=\left|\underline{{\mathbf{Z}}}\right\rangle\left\langle\underline{{\mathbf{Z}}}\right|$   then  

$$
\begin{array}{r l}&{\mu_{y}(L_{z})=\mathrm{tr}(|\underline{{y}}\rangle\langle\underline{{y}}|\,|\underline{{z}}\rangle\langle\underline{{z}}|)}\\ &{\qquad\qquad=\mathrm{tr}(|\underline{{y}}\rangle\langle\underline{{y}}|\,|\underline{{z}}\rangle\langle\underline{{z}}|)}\\ &{\qquad\qquad=\langle\underline{{y}}\mid\underline{{z}}\rangle\mathrm{tr}(|\underline{{y}}\rangle\langle\underline{{z}}|)}\\ &{\qquad\qquad=\langle\underline{{y}}\mid\underline{{z}}\rangle\langle\underline{{z}}\mid\underline{{y}}\rangle}\\ &{\qquad\qquad=|\langle\underline{{y}}\mid\underline{{z}}\rangle|^{2}}\end{array}
$$  

as before. We can say that, a measure of the extent to which  $\mathbf{P}_{y}\rightarrow\mathbf{P}_{z}$  is given by  $\mathbb{1}{\mathrm{-}}\mathbb{r}(\mathbf{P}_{y}\mathbf{P}_{z})$  . At this point we are free to abandon the information-theoretic point of view and simply use the probability measure, which in all cases is given by 1 minus the information. The probability of course is a measure of the certainty of the implication in this context.  

Now in Chapter 4 we showed that    ${\bf P}_{y}\,\rightarrow\,{\bf P}_{z}$   can itself be considered a projection onto a subspace, that is,  $\mathbf{P}_{y}\rightarrow\mathbf{P}_{z}$   is itself a self-adjoint idempotent linear operator, and as such can by Gleason’s Theorem be used to induce a (probability) measure on the space. It brings the logic on the space within the scope of algebraic manipulation. Each logical operator has an algebraic equivalent, and Gleason’s Theorem ensures that we can induce a probability measure consistent with the logic.  

So far we have considered the extent to which a single object plausibly implies another. Consider now the case when we have a set of objects    $Y=$   $\{{\underline{{\bf y}}}_{1},\ldots,{\underline{{\bf y}}}_{k}\}$   in which each object is of variable importance as the antecedent of the inference, that is, we weight their importance with  $\alpha_{i}$   such that  $\sum\alpha_{i}=1.$  . To represent canonically such a mixture 14   of objects we use the  density operator introduced earlier, namely  

$$
\rho=\alpha_{1}\mathbf{P}_{1}+\cdot\cdot\cdot+\alpha_{k}\mathbf{P}_{k},
$$  

where  $\mathbf{P}_{i}$   is the projector onto  $\underline{{\mathrm{y}}}_{i}$  . Once again Gleason’s Theorem tells us that the probability measure of any subspace  $L_{z}$   is given by  

$$
\begin{array}{r l}&{\mu(L_{z})=\mathrm{tr}(\rho\mathbf{P}_{z})}\\ &{\qquad=\alpha_{1}\mathrm{tr}(\mathbf{P}_{1}\mathbf{P}_{z})+\cdot\cdot\cdot+\alpha_{k}\mathrm{tr}(\mathbf{P}_{k}\mathbf{P}_{z})}\\ &{\qquad=\alpha_{1}\mu_{1}(L_{z})+\cdot\cdot\cdot+\alpha_{k}\mu_{k1}(L_{z})}\\ &{\qquad=\alpha_{1}|\langle\underline{{\sf z}}\mid\underline{{\mathbf{y}}}_{1}\rangle|^{2}+\cdot\cdot\cdot+\alpha_{k}|\langle\underline{{\sf z}}\mid\underline{{\mathbf{y}}}_{k}\rangle|^{2},}\end{array}
$$  

which is the appropriate mixture of the probabilities associated with the indi- vidual objects  $\underline{{\boldsymbol{\mathrm{y}}}}_{i}$  . We realise that the projectors    $\mathbf{P}_{i}$   do not need to project onto 1-dimensional subspaces, they could equally project onto ﬁnite-dimensional subspaces of dimension greater than one. The same applies to    $\mathbf{P}_{z}$  , which could be replaced by a subspace of greater dimension.Whenthishappens,itisexpress- ing the fact that there is a certain amount of ignorance about the objects involved. The probability calculation carries through as before.  

As already noted,    $\rho$  , the density operator, is a linear operator in the space of linear operators and  

$$
\begin{array}{r}{\mathrm{tr}(\rho\mathbf{P}_{z})=\langle\rho\mid\mathbf{P}_{z}\rangle,}\end{array}
$$  

where the inner product is now on the space of linear operators.   What has emerged is that our analysis is done very simply in the dual space of linear oper- ators with a natural geometric interpretation in the base space of objects. This very abstract way of proceeding is useful when trying to prove mathematical results about the constructs, but in practical information retrieval one is more likely to work in the base space of objects.  

# Ostensive retrieval  

In an earlier paper (Campbell and Van Rijsbergen, 1996) a model of retrieval based on  ostension  (Quine, 1969) was proposed. Simply, this model assumes that a user browsing in information space will point at objects which are relevant. As the search enlarges, the user will have pointed at an ever increasing number of objects. The probability of relevance of an ‘unseen’ object is a function of the characteristics of the objects seen thus far. To make the process work a function is needed that will incorporate new relevance assessments, and at each stage calculate the probability of the objects to be considered next. This is somewhat like the pseudo-relevance feedback discussed earlier. For a detailed account see Campbell and Van Rijsbergen (1996). We are only interested in the formalisation of the function that estimates the probability of relevance.  

If    $Y=\{\underline{{\mathbf{y}}}_{1},.\.\.\,,\underline{{\mathbf{y}}}_{k}\}$   are the objects encountered so far in the order 1 to    $k$  , then the impact of the set    $Y$   on the probability calculation can be summarised by a density operator:  

$$
\begin{array}{l}{\rho=\alpha_{1}|\underline{{\bf y}}_{1}\rangle\langle\underline{{\bf y}}_{1}|+\cdot\cdot\cdot+\alpha_{k}|\underline{{\bf y}}_{k}\rangle\langle\underline{{\bf y}}_{k}|,}\\ {\mathrm{where}\;\sum\alpha_{i}=1}\end{array}
$$  

and the values    $\alpha_{i}$   are scaled to increase proportionately. For example,    $\alpha_{i}=$   $\textstyle\left({\frac{1}{2}}\right)^{k-i+1}$    would double the relative weight each time    $i$   was inc ented by 1 up to  k . However, these weights do not sum to one, the sum is  $\textstyle\left({\frac{1}{2}}\right)^{k}$     short of one. So if we corrected each  $\alpha_{i}$   to  $\begin{array}{r}{\alpha_{i}+\frac{1}{k}\left(\frac{1}{2}\right)^{k}}\end{array}$   +  they would add to one.  

To calculate the probability associated with an unseen object x, we once again compute  $\operatorname{tr}(\rho\vert\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{x}}}\vert)$   for any x.  

In the original Campbell and Van Rijsbergen paper we used a slightly dif- ferent calculation for the probabilities involved:  

$$
{\begin{array}{r l}&{p_{i}=P(x_{i}=1\,|\,\mathrm{Real})}\\ &{\quad=\displaystyle\sum_{j=1}^{k}x_{i j}\left({\frac{P_{y_{j}}(\mathrm{Re})}{\displaystyle\sum_{u=1}^{k}P_{y_{u}}(\mathrm{Re})}}\right)}\\ &{\quad=\displaystyle\sum_{j=1}^{k}\alpha_{j}x_{i j}.}\end{array}}
$$  

Here the set of seen documents totalling  $k$   in number were all assumed relevant, and the  $\alpha_{i}$   were assumed be a speciﬁc discounting function as explained above. Thus for each index term    $i$   occurring in document  $j$  ,  $x_{i j}=1$  , and the    $\alpha_{j}$   made a contribution, whereas if the  i th term not occur in document  $j$   no contribution accrues, that is,  $x_{i j}=0$  .  

The calculation based on the geometry of the space is slightly different. To estimate  $p_{i}$  , we use  

$$
\begin{array}{r l}&{p_{i}\approx\mathrm{tr}(\rho|x_{i}\rangle\langle x_{i}|)}\\ &{\quad=\displaystyle\sum_{j=1}^{k}\alpha_{j}\mathrm{tr}(|y_{j}\rangle\langle y_{j}||x_{i}\rangle\langle x_{i}|)}\\ &{\quad=\displaystyle\sum_{j=1}^{k}\alpha_{j}\mathrm{tr}(|y_{j}\rangle\langle y_{j}|\langle x_{i}\rangle\langle x_{i}|)}\\ &{\quad=\displaystyle\sum_{j=1}^{k}\alpha_{j}|\langle y_{j}|x_{i}\rangle|^{2}.}\end{array}
$$  

Now if  $y_{j}$   and  $x_{i}$   are orthogonal then    $\langle y_{j}\mid x_{i}\rangle=0$   and no contribution accrues to  $p_{i}$  . When    $\langle y_{j}\mid x_{i}\rangle\neq0$   the value of  |⟨  $|\langle y_{j}\mid x_{i}\rangle|^{2}$   | ⟩|   modiﬁed by  $\alpha_{j}$   contributes to  $p_{i}$  . Notice again that this is different from the Campbell and Van Rijsbergen ion. Whereas in the original paper  $x_{i j}=0$   or 1, here we have  $x_{i j}=|\langle y_{j}\mid x_{i}\rangle|^{2}$   = |⟨  | ⟩|   which is a value in the interval [0, 1]. Thus it is a generalisation of the original model and it would not be difﬁcult to modify the generalised formula for  $x_{i j}$   so that it replicated the original one.  

# Further reading and future research  

The foregoing chapter has been well referenced at the appropriate places. The centre piece of it is undoubtedly Gleason’s Theorem and its application to problems in IR. Apart from Gleason’s original 1957 paper, there is the ele- mentary proof by Cooke  et al . (1985), and the constructive proof by Richman and Bridges (1999). Several books develop the requisite mathematics before explaining Gleason’s Theorem; good examples are Cohen (1989), Jauch (1968), Parthasarathy (1992) and Varadarajan (1985). There is an important special case of the theorem where the measure is a probability measure, and it is deﬁned in terms of a density operator. Density measures are extensively used in quan- tum mechanics but infrequently explained properly. For example, d’Espagnat (1976) gives a ‘density matrix formalism’ for QM but unfortunately devotes very little space to explaining the nature of density operators. Luckily, a thor- ough and standard account may be found in the widely used textbook for QM by Cohen-Tannoudji  et al . (1977).  

One of the motivations for writing this book is to lay the foundations for further research in IR using some of the tools presented here. There are several areas for immediate development; we will just mention three:  language mod- elling  (Croft and Lafferty, 2003),  probability of conditionals  and  information theory . These three are not unrelated. In Lavrenko and Croft (2003) the point is speciﬁcally made: ‘The simple language modelling approach is very simi- lar to the logical implication and inference network models, . . .’. Language models, on the one hand, deal with producing generative models for  $P(Q\,|\,D)$  , where    $Q$   is the query and  $D$   a document. On the other hand, logical models are concerned with evaluating  $P(D\rightarrow Q)$  , where   $\hookrightarrow'$   may be a non-standard impli- cation such as was fully described in Chapter 5. There seems to be an intimate, largely unknown, connection between    $P(Q\,|\,D)$   and  $P(D\to Q)$  , and one of the missing ingredients is an appropriate measure of information, which is required for the evaluation of the conditional by the Logical Uncertainty Principle (Van Rijsbergen, 1992).  

In quantum mechanics conditional probability is deﬁned with the help of Gleason’s Theorem as  

$$
P^{\mathrm{W}}(P\,|\,P^{\prime})=\frac{\mathrm{tr}(P^{\prime}{\bf W}P^{\prime}P)}{\mathrm{tr}({\bf W}P^{\prime})}
$$  

for events    $P$   and  $P^{\prime}$  , both projections or their corresponding subspaces. The way to read this equation in IR is as follows. W is a density matrix which may represent a mixture of states, think of it as deﬁning a context,  $P^{\prime}$    represents an observable that is measured, and thus brings about a transformation in    $\mathbf{W}$  :  

$$
\mathbf{W}\rightarrow\frac{P^{\prime}\mathbf{W}P^{\prime}}{\mathrm{tr}(\mathbf{W}P^{\prime})},
$$  

which by Gleason’s Theorem gives us the formula for    $P^{\mathrm{W}}(P\,|\,P^{\prime})$   shown above. Compare this with the unconditional probability  $P^{\mathrm{W}}(P)$   in the context of    $\mathbf{W}$  ,  

$$
P^{\mathrm{W}}(P)=\operatorname{tr}(\mathbf{W}P).
$$  

So here we have an algorithmic (or algebraic) representation of the conditional probability for events in Hilbert space. This general form of conditioning is called L¨ uders’ rule (L¨ uders, 1951), and it has a number of special cases, one of which is Von Neumann’s projection postulate (see Bub, 1997, 1982, for details). Also, when  W  indeed represents a mixture the rule is similar to Jeffrey Condi- tionalisation (Jeffrey, 1983, Van Fraassen, 1991, Van Rijsbergen, 1992). In gen- eral  W  represents a context where it might be a number of relevant documents, and  $P^{\mathrm{W}}(P\,|\,P^{\prime})$   would then represent the probability of  $P$  given  $P^{\prime}$    in that context.  

Ostensive retrieval could be viewed in terms of conditional is ation, that is,  W could represent a weighted combination of the documents touched so far, and  $P^{\mathrm{W}}(P\,|\,P^{\prime})$   would be the probability of an unseen document  $P=|\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{x}}}|$  , given that we have observed the last one,  $P^{\prime}=|\underline{{\mathbf{y}}}\rangle\langle\underline{{\mathbf{y}}}|$  .  

Language modelling can be analysed in a similar way, but now    $P=|\underline{{\mathbf{q}}}\rangle\langle\underline{{\mathbf{q}}}|$  represents the query, and    $P=|\underline{{\mathsf{d}}}\rangle\langle\underline{{\mathsf{d}}}|$   is a document, whereas    $\mathbf{W}$   would be some relevant documents. Again a conditional probability is calculated within a context.  

For more details on the Projection Postulate the reader should consult the now extensive literature: Gibbins (1987), Herbut (1969, 1994), Martinez (1991) and Teller (1983).  

It is an interesting research question to investigate to what extent    $P(D\to Q)$  , when    $D\rightarrow Q$   is the Stalnaker conditional from Chapter 5, will function as a language model, that is, an alternative to  $P(Q\,|\,D)$  . The accessibility relation that underlies the evaluation of  $D\rightarrow Q$   is deﬁned in terms of a metric derived from the inner product on the Hilbert space (see also Herbut, 1969). Such a metric may be deﬁned in information-theoretic terms (Amari and Nagaoka, 2000 and Wootters, 1980a). An exploration of this largely unexplored area may well lead to a reasonable measure for the missing information in the Logical Uncertainty Principle (Van Rijsbergen, 2000).  

The technique of imaging that was used to calculate    $P(D\to Q)$   in ear- lier papers could also be reformulated algebraically making use of Gleason’s Theorem and the fact that    $D\rightarrow Q$   is a projection operator and corresponds to a subspace of the Hilbert space. Some guidance for this may be found in Bigelow (1976, 1977).  

# Appendix I Linear algebra  

In any particular theory there is only as much real science as there is mathematics  

Immanuel Kant  

Much of the mathematics in the main part of this book is concerned with Hilbert space. In general a Hilbert space is an inﬁnite-dimensional space, but for most practical purposes we are content to work with ﬁnite-dimensional vector spaces, which indeed can be generalised to inﬁnite-dimensional ones. In some IR applications, such as content-based image retrieval, inﬁnite spaces may well arise, so there is good reason not to exclude them.  

Here we concentrate on ﬁnite-dimensional vector spaces and collect together for reference some of the elementary mathematical results relevant to them. For this our intuitions deriving from 3-dimensional Euclidean space will stand us in good stead. The best starting point for an understanding of a vector space is to state its axioms.  

# Vector space  

Deﬁnition A vector space is a set    $V$   of objects called  vectors  satisfying the following axioms.  

1  What follows is mostly taken from Halmos (1958) with small changes, but equivalent formulations can be found in many texts on linear algebra, for example, Finkbeiner (1960), Mirsky (1990), Roman (1992), Schwarz  et al . (1973), Birkhoff and MacLane (1957) and Sadun (2001), to name but a few. A good introduction that is slanted towards physics and quantum mechanics is Isham (1989). A readable and popular introduction is Chapter 4 of Casti (2000). Extensions to Hilbert space can be found in Debnath and Mikusinski (1999), Simmons (1963), Jordan (1969) and Bub (1997, Appendix). The Appendix to Redhead (1999) may also prove useful.  

(A) To every pair,  $\underline{{\mathbf{X}}}$   and  $\underline{{\boldsymbol{\mathrm{y}}}}$  , of vectors in    $V$   there corresponds a vector   $\underline{{\boldsymbol{\mathbf{x}}}}+\underline{{\boldsymbol{\mathbf{y}}}}$  , called the sum of  $\underline{{\mathbf{X}}}$   and  $\underline{{\boldsymbol{\mathrm{y}}}}.$  , in such a way that  

(1) addition is commutative,   $\underline{{\boldsymbol{\mathrm{x}}}}+\underline{{\boldsymbol{\mathrm{y}}}}=\underline{{\boldsymbol{\mathrm{y}}}}+\underline{{\boldsymbol{\mathrm{x}}}},$  , (2) addition is associative,  $\underline{{\mathbf{x}}}+(\underline{{\mathbf{y}}}+\underline{{\mathbf{z}}})=(\underline{{\mathbf{x}}}+\underline{{\mathbf{y}}})+\underline{{\mathbf{z}}},$  , (3) there exists in    $V$   a unique vector    (called the origin) such that  $\underline{{\mathbf{x}}}+\boldsymbol{\Phi}=\underline{{\mathbf{x}}}$   for every vector  $\underline{{\mathbf{X}}}$   in    $V.$  , (4) to every vector  $\underline{{\mathbf{X}}}$   in  $\mathrm{v}$   there corresponds a unique vector    $-\underline{{\mathbf{X}}}$   such that  ${\underline{{\mathbf{x}}}}+(-{\underline{{\mathbf{x}}}})=\Phi$  .  

(B) To every pair    $\alpha$   and   $\underline{{\mathbf{X}}}$  , where    $\alpha$   is a scalar and  $\underline{{\mathbf{X}}}$   is a vector in    $V.$  , there corresponds a vector  $\alpha_{-}$  , called the product of    $\alpha$   and x, in such a way that  

(1) multiplication by scalars is associative,    $\alpha(\beta_{\underline{{\mathbf{X}}}})=(\alpha\beta)_{\underline{{\mathbf{X}}}}.$  , (2)   $\boldsymbol{1}\underline{{\mathbf{x}}}=\underline{{\mathbf{x}}}$   for every  $\underline{{\mathbf{X}}}$  , (3) multiplication by  scalars  is distributive with respect to vector addition,  $\alpha(\underline{{\mathrm{x}}}+\underline{{\mathrm{y}}})=\alpha\underline{{\mathrm{x}}}+\alpha\underline{{\mathrm{y}}},$  , (4) multiplication by  vectors  is distributive with respect to scalar addition  $(\alpha+\beta)_{\underline{{\mathbf{X}}}}=\alpha_{\underline{{\mathbf{X}}}}+\beta_{\underline{{\mathbf{X}}}}.$  

In the main body of the text (Chapter 3) we introduce    $n$  -dimensional vectors and illustrate arithmetic operations with them. It is an easy exercise to verify that the set of  $n$  -dimensional vectors realised by  $n$  -tuples of complex numbers satisfy all the axioms of a vector space. Thus if we deﬁne for   ${\underline{{\mathbf{x}}}}=(x_{1},\dots,x_{n})^{\mathrm{T}}$  and   $\underline{{\mathbf{y}}}=(y_{1},.\,.\,.\,,y_{n})^{\mathrm{T}}$  ,  

$$
\begin{array}{r l}&{\underline{{\mathrm{x}}}+\underline{{\mathrm{y}}}=(x_{1}+y_{1},.\,.\,.\,,x_{n}+y_{n})^{\mathrm{T}},}\\ &{\qquad\alpha\underline{{\mathrm{x}}}=(\alpha x_{1},.\,.\,.\,,x_{n})^{\mathrm{T}},}\\ &{\qquad\Phi=(0,.\,.\,.\,,0)^{\mathrm{T}},}\end{array}
$$  

the axioms A and B above are satisﬁed for the set of  $n$  -tuples and hence    $C^{n}$    is a vector space. In many ways this    $n$  -dimensional space is the most important vector space since invariably it is the one used to illustrate and motivate the intuitions about abstract vector spaces.  

Another simple example of a vector space is the space of  n th order polyno- mials, including the polynomial identically zero. For example, if  $n=2$  , then  

$$
\begin{array}{r l}&{P_{1}(x)=a_{0}+a_{1}x+a_{2}x^{2},}\\ &{P_{2}(x)=b_{0}+b_{1}x+b_{2}x^{2},}\\ &{P_{1}(x)+P_{2}(x)=(a_{0}+b_{0})+(a_{1}+b_{1})x+(a_{2}+b_{2})x^{2}=P_{12},}\end{array}
$$  

and    $P_{12}$   is another second-order polynomial.  

# Hilbert space  

A Hilbert space is a simple extension of a vector space. It requires the deﬁnition of an  inner product  on the vector space (see Chapter 3) which enables it to be called an inner product space. An example of an inner product on a ﬁnite vector space between  $\underline{{\mathbf{X}}}$   and y is  

$$
({\underline{{\mathbf{x}}}},{\underline{{\mathbf{y}}}})=\sum_{i=1}^{n}{\bar{x}}_{i}y_{i},\quad{\mathrm{~where~}}{\bar{x}}_{i}{\mathrm{~is~the~complex~conjugate~of~}}x_{i}.
$$  

If we now impose the  completeness condition  on an inﬁnite inner product space  $V$  : that is, for every sequence of vectors   $\left(\underline{{\mathbf{v}}}_{n}\right)$  , if    $\|\underline{{\mathtt{v}}}_{m}-\underline{{\mathtt{v}}}_{m}\|\to0$   as  $n$   $\cdot,m\rightarrow0$  then there exists a vector v such that    $\|\ \underline{{\mathbf{v}}}_{n}-\underline{{\mathbf{v}}}\ \|\to0$  .  

The most straightforward example of a Hilbert space is the set of inﬁnite sequences  $(x_{1},.\;.\;.\;,x_{k},.\;.\;.)$   of complex numbers such that  $\sqrt{\Sigma_{i=1}^{\infty}|x_{i}|^{2}}$   is ﬁnite, or equivalently, such    $\textstyle\sum_{i=1}^{\infty}\lvert x_{i}\rvert^{2}$  | |  converges. Addition of sequences is deﬁned = component-wise, that is, for   $\mathtt{x}=(x_{1},.\ .\ .\ ,x_{k},.\ .\ .)$   and  $\underline{{\mathbf{y}}}=(y_{1},.\;.\;.\;,y_{k},.\;.\;.)$   we have  $\underline{{\boldsymbol{\mathrm{x}}}}+\underline{{\boldsymbol{\mathrm{y}}}}=\left(x_{1}+y_{1},\ldots,x_{k}+y_{k},\ldots\right)$  ; similarly for  $\theta$   an  $\alpha_{\underline{{\mathbf{X}}}}$  . The importance of this Hilbert space of square-summable sequences, called  $l_{2}$  , derives from the fact that any abstract Hilbert space is isomorphic to it (Schmeidler, 1965). Hence if one imagines a Hilbert space in this concrete form one cannot go far wrong. An inner product on it is a simple extension of the one on the ﬁnite space given earlier:  

$$
(\underline{{\mathbf{x}}},\underline{{\mathbf{y}}})=\sum_{i=1}^{\infty}\bar{x}_{i}y_{i}.
$$  

# Operators  

A linear operator    $\mathbf{T}$   on a vector space    $V$   is a correspondence that assigns to every vector  $\underline{{\mathbf{Z}}}$   in    $V$   a vector    $\mathbf{T}_{\underline{{\mathbf{Z}}}}$   in    $V.$  , in such a way that  

$$
\mathbf{T}(\alpha_{\underline{{\mathbf{X}}}}+\beta\underline{{\mathbf{y}}})=\alpha\mathbf{T}_{\underline{{\mathbf{X}}}}+\beta\mathbf{T}_{\underline{{\mathbf{y}}}}
$$  

for any vectors  $\underline{{\mathbf{X}}}$   and y and scalars  $\alpha$   and  $\beta$  . The most important class of linear operators for us are the  self-adjoint  operators. An adjoint    $\mathbf{T^{*}}$   of a linear operator  $\mathbf{T}$   is deﬁned by  

$$
(\mathbf{T}_{\mathbf{\Phi}\underline{{\mathbf{X}}}}^{*},\underline{{\mathbf{y}}})=(\underline{{\mathbf{x}}},\mathbf{T}\underline{{\mathbf{y}}});
$$  

and it is self-adjoint when   $\mathbf{T^{*}}=\mathbf{T}$  . Often the name  Hermitian  is used syn- onymously for self-adjoint. The Hermitian operators have a number of suit- able properties, such as that all their eigenvalues are real, which makes them suitable candidates as mathematical objects to represent observables in quantum mechanics and information space.  

# Linear functionals  

There is one ﬁnal abstract result that is often implicitly assumed, that is rarely explicitly stated, and it concerns linear functionals on a vector space. A  linear functional  on a vector    $V$   is a map  $f\colon V\to\Gamma$  , from    $V$   into the ﬁeld of scalars  $\Gamma$  , with the properties  

$$
f(\alpha\underline{{\mathbf{x}}}+\beta\underline{{\mathbf{y}}})=\alpha f(\underline{{\mathbf{x}}})+\beta f(\underline{{\mathbf{y}}}),\;\mathrm{for}\;\mathrm{all}\;\alpha,\beta\in\Gamma,\;\mathrm{and}\;\underline{{\mathbf{x}}},\underline{{\mathbf{y}}}\in V.
$$  

The set of linear functionals on a vector space is itself a vector space known as a  dual  space to    $V_{\cdot}$  , usually written    $V^{*}$   (Redhead, 1999, Appendix). If  $\underline{{\mathbf{X}}}\in\mathbf{V}$   and  $f\!\in\!\mathrm{V}^{*}$  , a 1:1 correspondence  $\varphi$   between    $V$   and    $V^{*}$   is deﬁned by writing  

The result is a theorem that for any  $f$  there exists an x and the  $\underline{{\mathbf{X}}}$   is unique. There is more about duality in Sadun (2001).  

At this point we can take a quick dip into the world of IR to illustrate the use of duality. Say we have deﬁned the usual cosine correlation on the space of documents to represent the inner product between documents. We can have a linear functional that associates with each document a scalar, and then the theorem tells us that for the particular inner product there is a vector   $\underline{{\mathbf{X}}}$   with respect to which the inner product with each document y will result in the same scalar value. The reverse is true too: the inner product between each  $\underline{{\boldsymbol{\mathrm{y}}}}$   and a given x will generate a linear functional on the space  $V.$   One way to interpret  $\underline{{\mathbf{X}}}$  is that it can represent the query as a vector on the document space.  

# Dirac notation  

We are now in a position to introduce the succinct Dirac notation that is used at various places in the book, especially in Chapter 6. Paul Dirac (1958) was responsible for introducing the ‘bra’ and ‘ket’ notation. A vector y in a Hilbert space    $\mathbf{H}$   is represented by    $|\underline{{\mathbf{y}}}\rangle$  , a ket. The linear functional  $f$  associated with   $\underline{{\mathbf{X}}}$  is denoted by    $\langle{\underline{{\mathbf{X}}}}|$  , the bra, thus forming the ‘bra(c)ket’    $\langle\underline{{\mathbf{x}}}\mid\underline{{\mathbf{y}}}\rangle$  the inner product. The bra (the linear functional) has the linearity property shown as follows in the Dirac notation:  

$$
\langle\underline{{\mathtt{x}}}|(\alpha\mid\underline{{\mathtt{y}}}\rangle+\beta\mid\underline{{\mathtt{z}}}\rangle)=\alpha\langle\underline{{\mathtt{x}}}\mid\underline{{\mathtt{y}}}\rangle+\beta\langle\underline{{\mathtt{x}}}\mid\underline{{\mathtt{z}}}\rangle.
$$  

The set of linear functionals is a vector space itself, as we observed above, and so they can be added and multiplied by complex numbers in the usual way:  

$$
[\alpha\langle\underline{{\mathsf{u}}}|+\beta\langle\underline{{\mathsf{v}}}|](|\underline{{\mathsf{z}}}\rangle)=\alpha\langle\underline{{\mathsf{u}}}\,|\,\underline{{\mathsf{z}}}\rangle+\beta\langle\underline{{\mathsf{v}}}\,|\,\underline{{\mathsf{z}}}\rangle.
$$  

The 1:1 mapping between    $V$   and    $V^{*}$  ,    $\varphi$   above, is often denoted by a star   \* , the same symbol used for indicating the adjoint of an operator. In the Dirac notation this rarely causes confusion, and if it does, it can be resolved by the judicious use of brackets.  

We have the two relations  

$$
\langle\underline{{\mathbf{x}}}|=(|\underline{{\mathbf{x}}}\rangle)^{*}\ \mathrm{and}\ |\underline{{\mathbf{x}}}\rangle=(\langle\underline{{\mathbf{x}}}|)^{*}.
$$  

The star operation is antilinear, reﬂecting the fact that the inner product is antilinear in its left argument,  

$$
\begin{array}{r}{(\alpha|\underline{{\mathbf{y}}}\rangle+\beta|\underline{{\mathbf{z}}}\rangle)^{*}=\alpha^{*}\langle\underline{{\mathbf{y}}}|+\beta^{*}\langle\underline{{\mathbf{z}}}|,}\\ {(\gamma\langle\underline{{\mathbf{u}}}|+\delta\langle\underline{{\mathbf{v}}}|)^{*}=\gamma^{*}|\underline{{\mathbf{u}}}\rangle+\delta^{*}|\underline{{\mathbf{v}}}\rangle.}\end{array}
$$  

One ﬁnal piece of the Dirac notation is concerned with linear operators. The inner product of a vector  $\left|\underline{{\mathbf{X}}}\right\rangle$  in  $\mathbf{H}$   with the ket    $\mathbf{T}|\underline{{\mathbf{y}}}\rangle$  can be written as  

$$
(|\underline{{\mathbf{x}}}\rangle)^{*}\mathbf{T}|\underline{{\mathbf{y}}}\rangle=\langle\underline{{\mathbf{x}}}|\mathbf{T}|\underline{{\mathbf{y}}}\rangle.
$$  

$\langle\underline{{\mathbf{x}}}|\mathbf{T}|\underline{{\mathbf{y}}}\rangle$  is the famous ‘sandwich’ notation, which if it seems uninformative during a manipulation can always be replaced by the more elaborate left-hand side of its deﬁnition.  

# Dyads  

A special class of operators, known as  dyads , is particularly useful when it comes to deriving results using the Dirac notation. A dyad is the outer product of a ket with a bra, and can be deﬁned by  

$$
\begin{array}{r}{|\underline{{\mathtt{x}}}\rangle\langle\underline{{\mathtt{y}}}|\left(|\underline{{\mathtt{z}}}\rangle\right)=|\underline{{\mathtt{x}}}\rangle\langle\underline{{\mathtt{y}}}|\,\underline{{\mathtt{z}}}\rangle=\langle\underline{{\mathtt{y}}}|\underline{{\mathtt{z}}}\rangle|\underline{{\mathtt{x}}}\rangle.}\end{array}
$$  

Here the operator    $\left|\underline{{\mathbf{X}}}\right\rangle\left\langle\underline{{\mathbf{y}}}\right|$   is applied to a vector    $|\underline{{\mathbf{Z}}}\rangle$  to produce the vector    $\left|\underline{{\mathbf{X}}}\right\rangle$  multiplied by a scalar    $\langle\underline{{\mathbf{y}}}\ \rangle\ \underline{{\mathbf{Z}}}\rangle$  .  

Especially important dyads are the projectors, which are of the form    $|\underline{{\mathbf{u}}}\rangle\langle\underline{{\mathbf{u}}}|$  , where  $\underline{{\boldsymbol{\mathsf{u}}}}$   is the vector onto which the projection is made. For example,  

$$
\begin{array}{r}{|\underline{{\mathbf{u}}}\rangle\langle\underline{{\mathbf{u}}}|(|\underline{{\mathbf{z}}}\rangle)=|\underline{{\mathbf{u}}}\rangle\langle\underline{{\mathbf{u}}}\,|\,\underline{{\mathbf{z}}}\rangle=\langle\underline{{\mathbf{u}}}\,|\,\underline{{\mathbf{z}}}\rangle|\underline{{\mathbf{u}}}\rangle,}\end{array}
$$  

where the application of the projector to vector    $\left|\underline{{\mathbf{Z}}}\right\rangle$  results in    $\lvert\underline{{\mathbf{u}}}\rangle$  multiplied by a scalar. A projector of this kind is therefore a linear transformation that takes any vector and maps it onto another vector.  

Multiplying dyads is especially easy:  

$$
\begin{array}{r}{\vert\underline{{\mathbf{u}}}\rangle\langle\underline{{\mathbf{v}}}\vert\vert\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{z}}}\vert=\langle\underline{{\mathbf{v}}}\vert\,\underline{{\mathbf{x}}}\rangle\vert\underline{{\mathbf{u}}}\rangle\langle\underline{{\mathbf{z}}}\vert,}\end{array}
$$  

resulting in another dyad multiplied by the scalar    $\left\langle\underline{{\mathbf{v}}}\mid\underline{{\mathbf{X}}}\right\rangle$  . The multiplication quickly demonstrates that operators in general do not  commute , for  

$$
\begin{array}{r}{|\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{z}}}||\underline{{\mathbf{u}}}\rangle\langle\underline{{\mathbf{v}}}|=\langle\underline{{\mathbf{z}}}\,|\,\underline{{\mathbf{u}}}\rangle|\underline{{\mathbf{x}}}\rangle\langle\underline{{\mathbf{v}}}|,}\end{array}
$$  

and in general these two resulting dyads are not equal,  

$$
\langle\underline{{\mathbf{v}}}\mid\underline{{\mathbf{x}}}\rangle\,|\underline{{\mathbf{u}}}\rangle\,\langle\underline{{\mathbf{z}}}|\neq\langle\underline{{\mathbf{z}}}\mid\underline{{\mathbf{u}}}\rangle\,|\underline{{\mathbf{x}}}\rangle\,\langle\underline{{\mathbf{v}}}|.
$$  

# Useful identities in Dirac notation  

We now collect together a number of identities, using Dirac notation, that may prove useful. Let    $\{\varphi_{1},.\,.\,.\,,\varphi_{n}\}$   be an orthonormal basis for an    $n$  -dimensional Hilbert space, that is    $\sqrt{\langle\varphi_{k}|\varphi_{k}\rangle}=1$   and    $\langle\varphi_{i}\,|\,\varphi_{j}\rangle=\delta_{i j}$  . Although we produce these ﬁve identities for a ﬁnite space, they also hold for an inﬁnite-dimensional space.  

The set of dyads    $\left\{|\varphi_{1}\rangle\langle\varphi_{1}|,\,.\,.\,.\,\,,|\varphi_{n}\rangle\,\langle\varphi_{n}|\right\}$   is a set of projectors, one for each basis vector, and projecting onto that vector. They satisfy a completeness property, or resolution of identity, namely  

$$
\sum_{k=1}^{n}\mathinner{|{\varphi_{k}}\rangle}\mathinner{\langle{\varphi_{k}}|}=\mathbf{I},
$$  

where    $\mathbf{I}$   is the identity operator. They are also mutually orthogonal, that is  

$$
|\varphi_{i}\rangle\langle\varphi_{i}||\varphi_{j}\rangle\langle\varphi_{j}|=|\varphi_{i}\rangle\langle\varphi_{i}\,|\,\varphi_{j}\rangle\langle\varphi_{j}|=\delta_{i j}|\varphi_{i}\rangle\langle\varphi_{i}|.
$$  

The matrix representation of an operator  $\mathbf{T}$   with respect to an orthonormal basis such as    $\{\varphi_{1},.\,.\,.\,,\varphi_{n}\}$   is given by    $\langle\varphi_{j}|\mathbf{T}|\varphi_{k}\rangle$  , that is, it represents the  jk th element of the matrix.  

$$
|\psi\rangle=\left(\sum_{k=1}^{n}|\varphi_{k}\rangle\langle\varphi_{k}|\right)|\psi\rangle=\sum_{k=1}^{n}\langle\varphi_{k}\,|\,\psi\rangle|\varphi_{k}\rangle
$$  

shows how to resolve a vector into its components.  

$$
\langle\chi\mid\psi\rangle=\langle\chi\mid\sum_{k=1}^{n}\vert\varphi_{k}\rangle\langle\varphi_{k}\mid\psi\rangle=\sum_{k=1}^{n}\langle\chi\mid\varphi_{k}\rangle\langle\varphi_{k}\mid\psi\rangle
$$  

shows the inner product as a sum of pair-wise products of components.  

$$
\langle\varphi_{j}|\mathbf{T}|\psi\rangle=\langle\varphi_{j}|\mathbf{T}\sum_{k=1}^{n}|\varphi_{k}\rangle\langle\varphi_{k}|\psi\rangle=\sum_{k=1}^{n}\langle\varphi_{j}|\mathbf{T}|\varphi_{k}\rangle\langle\varphi_{k}\mid\psi\rangle
$$  

calculates the effect of    $\mathbf{T}$   on a vector    $|\psi\rangle$  in terms of matrix multiplication.  

$$
\mathbf{T}|\varphi_{j}\rangle=\sum_{k=1}^{n}|\varphi_{k}\rangle\langle\varphi_{k}|\mathbf{T}|\varphi_{j}\rangle=\sum_{k=1}^{n}\langle\varphi_{k}|\mathbf{T}|\varphi_{j}\rangle|\varphi_{k}\rangle
$$  

expresses the effect of    $\mathbf{T}$   on the  j th basis vector as a linear combination of the basis vectors with matrix elements as weights.  

$$
\langle\varphi_{j}|{\bf T}{\bf S}|\varphi_{k}\rangle=\langle\varphi_{j}|{\bf T}\sum_{i=1}^{n}|\varphi_{i}\rangle\langle\varphi_{i}|{\bf S}|\varphi_{k}\rangle=\sum_{i=1}^{n}\langle\varphi_{j}|{\bf T}|\varphi_{i}\rangle\langle\varphi_{i}|{\bf S}|\varphi_{k}\rangle
$$  

illustrates the product of  $\mathbf{T}$   and  S  in terms of the product of the corresponding matrix representations.  

It is a good exercise in the use of Dirac notation to show that the ﬁve identities hold. For further details the reader should consult Jordan (1969). An explanation of how the Dirac notation relates to standard mathematical notation for vector spaces is quite hard to ﬁnd, but one of the most recent can be found in Sadun (2001). Dirac (1958) himself of course explained and motivated the notation in his groundbreaking book, where it was developed along with an introduc- tion to quantum mechanics. The recent book by Grifﬁths (2002) has a clear explanation, but again it is intertwined with details of quantum mechanics. Developing an understanding of the Dirac notation is well worthwhile as it opens up many of the books and papers in quantum mechanics, especially the classics. One of the greatest is Von Neumann’s (1983), which uses the notation to great effect to discuss the foundations of quantum mechanics. The power of the notation comes from the fact that it accomplishes some very compli- cated manipulations whilst at the same time taking care of the ‘bookkeeping’, thus making sure, almost by sleight of hand, that mathematical correctness is preserved.  

A good example of the power of the Dirac notation shows in the derivation of the Cauchy–Schwartz inequality, which will be used in the next appendix.  

# Cauchy–Schwartz inequality  

The Cauchy–Schwartz inequality states that for two vectors    $|\varphi\rangle$  and    $|\Psi\rangle$  we have    $|\langle\varphi\,|\,\psi\rangle|^{2}\leq\langle\varphi\,|\,\varphi\rangle\langle\psi\,|\,\psi\rangle$  . To derive this result, construct a orthonormal basis    $\{\varphi_{1},.\,.\,.\,,\varphi_{n}\}$   for the Hilbert space. Let    $\vert\varphi_{1}\rangle=\vert\psi\rangle/\sqrt{\langle\psi\mid\psi\rangle}$  ,  then  

$$
\begin{array}{l}{{\displaystyle\langle\varphi\,|\,\varphi\rangle\langle\psi\,|\,\psi\rangle=\langle\varphi|\sum_{i}|\varphi_{i}\rangle\langle\varphi_{i}||\varphi\rangle\langle\psi\,|\,\psi\rangle}}\\ {{\displaystyle\qquad\qquad=\sum_{i}\langle\varphi\,|\,\varphi_{i}\rangle\langle\varphi_{i}\,|\,\varphi\rangle\langle\psi\,|\,\psi\rangle}}\\ {{\displaystyle\qquad\qquad\geq\frac{\langle\varphi\,|\,\psi\rangle\langle\psi\,|\,\varphi\rangle}{\langle\psi\,|\,\psi\rangle}\langle\psi\,|\,\psi\rangle}}\\ {{\displaystyle\qquad\qquad=\langle\varphi\,|\,\psi\rangle\langle\psi\,|\,\varphi\rangle=|\langle\varphi\,|\,\psi\rangle|^{2},}}\end{array}
$$  

where we have used the resolution of the identity    $\mathbf{I}$  , and ignored all the (non-negative) terms in the sum bar the ﬁrst.  

# Appendix II Quantum mechanics  

One should keep the need for a sound mathematical basis dominating one’s search for a new theory. Any physical or philosophical ideas that one has must be adjusted to ﬁt the mathematics. Not the other way around. Dirac, 1978 .  

This appendix will give a brief, highly simpliﬁed introduction to a number of the principles underlying quantum theory. It is convenient to collect them here independent of information retrieval. We will use the Dirac notation introduced in the previous appendix to express the necessary mathematics. Before examining the few principles underlying quantum mechanics let us make two comments. The ﬁrst is that there is no general agreement about whether probabilistic quantum statements apply to individual isolated systems or only to ensembles of such systems identically prepared. The second com- ment is that there is no distinct preference whether to develop quantum the- ory fully in terms of vectors in a Hilbert space, or in terms of the density operators applied to that space. We will not take a strong position on either division. For convenience we will assume that statements are applicable to single systems, and that when it suits, either vectors or density operators can be used.  

To begin with we will consider only pure states of single systems and observ- ables with discrete non-degenerate spectra.   This will keep the mathematics simple.  

There are four signiﬁcant fundamental concepts to consider: physical states, observables, measurements and dynamics; and of course the interplay between these.  

# Physical states  

A quantum state is the complete and maximal summary of the characteristics of the quantum system at a moment in time. Schr¨ odinger, see Wheeler and Zurek (1983), already held this view: ‘It (  $\psi$  -function) is now the means for predicting probability of measurement results. In it is embodied momentarily- attained sum of theoretically based future expectation, somewhat as laid down in a catalogue.’ The state of a system is represented mathematically by a unit vector    $|\varphi\rangle$  in a complex Hilbert space. That is, the states are such that  

$$
\|\varphi\|^{2}=\langle\varphi\,|\,\varphi\rangle=1.
$$  

The ensemble interpretation would say that the ensemble of identically prepared systems is represented by    $|\varphi\rangle$  . The same physical state as    $|\varphi\rangle$  is represented by  $\mathrm{e}^{\mathrm{i}\theta}\left|\varphi\right\rangle$  , its norm remains unity, and    $\theta$   is called the phase factor.  

# Observables  

These are represented by self-adjoint operators on the Hilbert space. It is assumed that every physical property that is to be measured is representable by such an operator, and that the spectrum of the operator comprises all possible values that can be found if the observable is measured. Thus, certain values called eigenvalues of the self-adjoint operator, which are all real, are all the out- comes of a measurement that are possible. The eigenvectors corresponding to the eigenvalues, are called the eigenstates of the system. A famous postulate 3   of Von Neumann required that immediately after a measurement a system could be deemed to be in the eigenstate corresponding to the observed eigenvalue. This would ensure that a measurement of the same observable immediately after its ﬁrst measurement would produce the same eigenvalue with probability 1.  

# Measurements  

Let us assume that we have a physical system whose quantum state is described by the ket    $|\varphi\rangle$  , and suppose that we measure the observable  T  which is repre- sented by the self-adjoint operator  T . In classical physics such a measurement would produce a deﬁnite result. However, in quantum theory the outcome of a measurement can only be predicted with a certain probability, making the claim that measurement is intrinsically probabilistic, and that the probability of outcome of a measurement depends on the state of the system, that is, it depends on    $|\varphi\rangle$  . This fundamental relationship is codiﬁed in the following manner for  $n$  -dimensional operators with a non-degenerate spectrum  

$$
P_{\varphi}(\mathbf{T},\lambda_{i})=\left\langle\varphi\mid\mathbf{E}_{i}^{\mathrm{T}}\varphi\right\rangle=\langle\varphi\mid\psi_{i}\rangle\langle\psi_{i}\mid\varphi\rangle=|\langle\varphi\mid\psi_{i}\rangle|^{2}
$$  

$\varphi$  is the normalised vector in Hilbert space representing the system,  

$\mathbf{T}$  is the self-adjoint operator representing the observable  $\mathbf{T}$  , 5

  $\mathbf{E}_{i}^{\mathrm{T}}$  is the projector    $\left|\psi_{i}\right\rangle\left\langle\psi_{i}\right|$   onto the 1-dimensional subspace spanned by    $\psi_{i}$  ,

  $\psi_{i}$  is one of the  $n$   eigenvectors associated with    $\mathbf{T}$  , and

  $\lambda_{i}$  is the  i th eigenvalue associated with the  i th eigenvector    $\psi_{i}$  .  

$P_{\varphi}\ ({\bf T},\lambda_{i})$   is the probability that a measurement of  $\mathbf{T}$   conducted on a system in state    $\varphi$   will yield a result    $\lambda_{i}$   with a probability given by    $|\langle\varphi\mid\psi_{i}\rangle|^{2}$  . In an  $n$  -dimensional Hilbert space any vector    $\varphi$   can be expressed as a linear combi- nation of the basis vectors. The eigenvectors    $\{\psi_{1},.\,.\,.\,,\psi_{n}\}$   form an orthonormal basis and hence    $\varphi=c_{1}\psi_{1}+c_{2}\psi_{2}+\cdot\cdot\cdot+c_{n}\psi_{n}$   $c_{i}$   complex numbers such that    $\Sigma_{i=1}^{n}|\mathbf{c}_{i}|^{2}=1$   1, and hence  |⟨  $|\langle\varphi\,|\,\psi_{i}\rangle|^{2}=|c_{i}^{*}c_{i}|=|c_{i}|^{2}$   | ⟩|  = | | = | | . Observe = that the probabilities sum to unity, as they must.  

From this algorithm for calculating the probability  $P_{\varphi}(.\,,.)$   it is immediately possible to derive the statistical quantities,  expected value  and  variance  of an observable, which we will need below to derive the famous Heisenberg Uncertainty Principle. The expected value    $\langle\mathbf{T}\rangle$  of an obervable    $\mathbf{T}$   is calculated as follows:  

$$
{\begin{array}{r l}&{\langle\mathbf{T}\rangle=\displaystyle\sum_{i=1}^{n}|\langle\varphi\,|\,\psi_{i}\rangle|^{2}\lambda_{i}=\sum_{i=1}^{n}\langle\varphi|\mathbf{E}_{i}^{\mathrm{T}}|\varphi\rangle\lambda_{i}}\\ &{\quad=\langle\varphi|\displaystyle\sum_{i=1}^{n}\lambda_{i}\mathbf{E}_{i}^{\mathrm{T}}|\varphi\rangle}\\ &{\quad=\langle\varphi|\mathbf{T}|\varphi\rangle.}\end{array}}
$$  

The last step in the derivation above is given by the Spectral Decomposition Theorem (see Chapter 4).  

The variance of a quantity is usually a measure of the extent to which it deviates from the expected value. In quantum mechanics the variance   $(\Delta\mathbf{T})^{2}$    of an observable  $\mathbf{T}$   in state  $\varphi$   is deﬁned as  

$$
\begin{array}{r}{(\Delta\mathbf{T})^{2}=\langle\mathbf{T}\varphi-\langle\mathbf{T}\rangle\varphi\,|\,\mathbf{T}\varphi-\langle\mathbf{T}\rangle\varphi\rangle=\|\mathbf{T}\varphi-\langle\mathbf{T}\rangle\varphi\|^{2}.}\end{array}
$$  

Let us demonstrate the expected value and variance with some examples. If the system is in one of its eigenstates, say  $\left|{\psi_{i}}\right\rangle$  , then for a measurement of the observable    $\mathbf{T}$   you expect    $\langle\mathbf{T}\rangle$  to be  $\lambda_{i}$   with zero variance, that is with complete certainty. Let us check this:  

$$
\begin{array}{r l}&{\langle\mathbf{T}\rangle=\langle\psi_{i}|\mathbf{T}|\psi_{i}\rangle=\langle\psi_{i}\mid\lambda_{i}\psi_{i}\rangle=\lambda_{i}\langle\psi_{i}\mid\psi_{i}\rangle=\lambda_{i}\operatorname{because}\,\langle\psi_{i}\mid\psi_{i}\rangle=0,}\\ &{(\Delta\mathbf{T})=\|\mathbf{T}\psi_{i}-\langle\mathbf{T}\rangle\psi_{i}\|=\|\mathbf{T}\psi_{i}-\lambda_{i}\psi_{i}\|=\|\mathbf{T}\psi_{i}-\mathbf{T}\psi_{i}\|=0.}\end{array}
$$  

Another interesting case is to look at the expectation of a projector onto an eigenvector    $\left|\psi_{i}\right\rangle$  when the system is in state    $|\varphi\rangle$  . Let    $\mathbf{T}_{i}=|\psi_{i}\rangle\langle\psi_{i}|$  ; then  

$$
\langle\vert\psi_{i}\rangle\langle\psi_{i}\vert\rangle=\langle\varphi\vert\,\psi_{i}\rangle\langle\psi_{i}\vert\,\varphi\rangle=\vert\langle\varphi\vert\,\psi_{i}\rangle\vert^{2},
$$  

which is the probability that a measurement of    $\mathbf{T}_{i}$   conducted on a system in state    $\varphi$   will yield a result  $\lambda_{i}$  . 6   Projection operators can be interpreted as simple questions that have a ‘yes’ or ‘no’ answer, because they have two eigenvalues, namely 1 and 0.  

$$
\begin{array}{r l}&{\mathbf{T}_{i}|\psi_{i}\rangle=|\psi_{i}\rangle\langle\psi_{i}\:|\:\psi_{i}\rangle=1|\psi_{i}\rangle;}\\ &{\mathbf{T}_{i}|\psi_{j}\rangle=|\psi_{i}\rangle\langle\psi_{i}\:|\:\psi_{j}\rangle=0|\psi_{i}\rangle\mathrm{\;because\;}\langle\psi_{i}\:|\:\psi_{j}\rangle=\delta_{i j}.}\end{array}
$$  

Given one such question    $\mathbf{T}_{i}$  ,    $\langle\mathbf{{T}}_{i}\rangle$  is the expected relative frequency with which the observable    $\mathbf{T}_{i}$   when measured will return an answer ‘yes’. Because any self-adjoint operator can be decomposed into a linear combination of pro- jectors, it implies that any observable can be reduced to a set of ‘yes’/‘no’ questions. Mackey(1963) developed this ‘ question-oriented ’ approach to quan- tum mechanics in some detail, constructing what he called question-valued measures.  

# Heisenberg Uncertainty Principle 7  

Surprisingly, this famous principle in quantum mechanics can be derived from Hilbert space theory for non-commuting self-adjoint operators without any reference to physics. It uses some simple facts about complex numbers and the Cauchy–Schwartz inequality (see Chapter 3). Its statement for two observables  $\mathbf{T}$   and  S  is that when    $\mathbf{T}$   and  S  are measured for a system whose quantum state is given by    $|\psi\rangle$  , then the product of the variances of  $\mathbf{T}$   and  S  are bounded from below as follows:  

$$
\begin{array}{r}{\Delta\mathbf{T}\Delta\mathbf{S}\geq\frac{1}{2}|\langle\psi|\mathbf{TS}-\mathbf{ST}|\psi\rangle|.}\end{array}
$$  

To derive it we need ﬁrst to introduce some notation and some elementary mathematical results. For any two observables    $\mathbf{A}$   and    $\mathbf{B}$   we can deﬁne the commutator    $[\mathbf{A},\mathbf{B}]$   and  anti-commutator    $\{\mathbf{A},\mathbf{B}\}$  

$$
\begin{array}{r}{[\mathbf{A},\,\mathbf{B}]\equiv\mathbf{A}\mathbf{B}-\mathbf{B}\mathbf{A},}\\ {\{\mathbf{A},\,\mathbf{B}\}\equiv\mathbf{A}\mathbf{B}+\mathbf{B}\mathbf{A}.}\end{array}
$$  

Let    $x$   and  $y$   be real variables and  $x+\mathrm{i}y$   a complex number.  

$$
\begin{array}{r l}&{~~~~\langle\psi|\mathbf{A}\mathbf{B}|\psi\rangle=x+\mathrm{i}y}\\ &{\langle\psi|[\mathbf{A},\mathbf{B}]|\psi\rangle=\langle\psi|\mathbf{A}\mathbf{B}|\psi\rangle-\langle\psi|\mathbf{B}\mathbf{A}|\psi\rangle=x+\mathrm{i}y-x+\mathrm{i}y=2\mathrm{i}y,}\\ &{\langle\psi|\{\mathbf{A},\mathbf{B}\}|\psi\rangle=\langle\psi|\mathbf{A}\mathbf{B}|\psi\rangle+\langle\psi|\mathbf{B}\mathbf{A}|\psi\rangle=x+\mathrm{i}y+x-\mathrm{i}y=2x.}\end{array}
$$  

Doing the complex number arithmetic, we can derive  

$$
|\langle\psi|[\mathbf{A},\mathbf{B}]|\psi\rangle|^{2}+|\langle\psi|\{\mathbf{A},\mathbf{B}\}|\psi\rangle|^{2}=4|\langle\psi|\mathbf{A}\mathbf{B}|\psi\rangle|^{2}.
$$  

By the Cauchy–Schwartz inequality, we get  

$$
\begin{array}{r}{|\langle\psi|\mathbf{AB}|\psi\rangle|^{2}\leq\langle\psi|\mathbf{A}^{2}|\psi\rangle\langle\psi|\mathbf{B}^{2}|\psi\rangle.}\end{array}
$$  

Combining this with the previous equation and dropping the term involving  $\{\mathbf{A},\mathbf{B}\}$  , we get  

$$
\begin{array}{r}{|\langle\psi|[\mathbf{A},\mathbf{B}]|\psi\rangle|^{2}\leq4\langle\psi|\mathbf{A}^{2}|\psi\rangle\langle\psi|\mathbf{B}^{2}|\psi\rangle.}\end{array}
$$  

7  See Heisenberg (1949) for an account by the master, and Popper (1982) for an enthusiastic critique.  

Now, to derive the principle we substitute    $\mathbf{A}=\mathbf{T}-\langle\mathbf{T}\rangle\mathbf{I}$   and    $\mathbf{B}=\mathbf{S}\,-\,\langle\mathbf{S}\rangle\mathbf{I},$  , where    $\mathbf{T}$   and    $\mathbf{S}$   are observables and  I  is the identity operator, and we get  

$$
\begin{array}{r l}&{(\Delta\mathbf{T})^{2}=\langle\psi|\mathbf{A}^{2}|\psi\rangle,}\\ &{(\Delta\mathbf{S})^{2}=\langle\psi|\mathbf{B}^{2}|\psi\rangle,}\\ &{\langle\psi|[\mathbf{A},\mathbf{B}]|\psi\rangle=\langle\psi|(\mathbf{T}-\langle\mathbf{T}\rangle\mathbf{I})(\mathbf{S}-\langle\mathbf{S}\rangle\mathbf{I})|\psi\rangle=\langle\psi|[\mathbf{T},\mathbf{S}]|\psi\rangle.}\end{array}
$$  

Substituting into the inequality above gives the Heisenberg Uncertainty Principle:  

$$
\Delta\mathbf{T}\Delta\mathbf{S}\geq\frac{|\langle\psi|[\mathbf{T},\mathbf{S}]|\psi\rangle|}{2}.
$$  

There are some interesting things to observe about this inequality and its deriva- tion. Time did not play a role in the derivation, so the result is independent of time. More importantly, one must be clear about its interpretation. The inequal- ity does not quantify how the measurement of one observable inteferes with the accuracy of another. The correct way to interpret it is as follows: when a large number of quantum systems are prepared in an identical state represented by  $|\psi\rangle$  , then peforming a measurement of  $\mathbf{T}$   on some of these systems, and  S  on others, the variances   $(\Delta\mathbf{T})^{2}$    and   $(\Delta\mathbf{S})^{2}$    will satisfy the Heisenberg inequality. It is important to emphasise once again that no physics was used in the deriva- tion, and the only extra mathematical results used, apart from standard Hilbert space geometry, were the Cauchy–Schwartz inequality and the fact that in gen- eral operators do not commute, that is,  $\mathbf{A}\mathbf{B}-\mathbf{B}\mathbf{A}\neq0$  . In the case where the operators do commute, the commutator [ A, B ] reduces to zero and the lower bound on the product of the variances is zero, and hence no bound at all. It is surprising that such a famous principle in physics is implied by the choice of mathematical representation for state and observable in Hilbert space.  

In this appendix the time evolution of the quantum state has been ignored, because in this book, time evolution is not considered. Nevertheless, it is impor- tant to remember that the evolution in time of a state vector    $|\psi\rangle$  is governed by the famous Schr¨ odinger equation. An excellent exposition of this equation may be found in Grifﬁths (2002).  

# Further reading  

The following is a list of references for further elementary, and in some cases more philosophical, introductions to quantum mechanics. The reader might like to consult the bibliography for the annotations with respect to each refer- ence. They are Aerts (1999), Baggott (1997), Barrett (1999), Greenstein and Zajonc (1997), Healey (1990), Heisenberg (1949), Isham (1995), Lockwood (1991), London and Bauer (1982), Murdoch (1987), Packel (1974), Pais (1991), Reichenbach (1944) and Van der Waerden (1968).  

Although this book is not about quantum computation, much of the literature referenced below contains excellent introductions to the mathematics for quan- tum mechanics in which the application to physics is minimized and instead the relationship with computing science is emphasized. Good examples are Bouwmeester  et al . (2001), Deutsch (1997), Grover (1997), Gruska (1999), Hirvensalo (2001), Lo  et al . (1998), Nielsen and Chuang (2000) and Pittenger (2000). Grover (1997) is not a book but a seminal paper on the application of quantum computation to searching.  

A book that deserves special mention is the one by Lomonaco (2002); although it is primarily an introduction to quantum computation, the ﬁrst chap- ter contains one of the best introductions to quantum mechanics this author has encountered.  

# Appendix III Probability  

Therefore the true logic for this world is the calculus of Probabilities which is, or ought to be, in a reasonable man’s mind.  

James Clerk Maxwell  

# Classical probability  

The usual starting point for classical probability theory is with Kolmogorov’s axioms, ﬁrst stated in his book published in 1933 and translated into English in 1950. Ever since then these axioms have been used and repeated in many publications, and may be considered as orthodoxy.   The Kolmogorov axioms deﬁne a probability measure on a ﬁeld    $\Im$  of sets, which is a collection of subsets of the set    $\Omega$  , the universe of basic events. This universe    $\Omega$   can be a set of anything; it is the subsets which are members of    $\Omega$   that are important.    $\Im$  is a ﬁeld  because it is closed with respect to the operations of complementation, countable union and intersection. Furthermore, it contains the empty set    $\Phi$  , and hence by complementation the entire set    $\Omega$  .  

We can nowdeﬁne a probability measure on    $\Im$  . It is a positive-valuedfunction  $\mu\colon\Im\to\mathfrak{H}^{+}$  , a mapping from the ﬁeld of subsets into the set of positive real numbers 2   with the following properties:  

$$
\mu(\Phi)=0;\quad\mu(\Omega)=1.
$$  

For any pairwise disjoint sequence    $S_{n}$  , that is  $S_{i}\cap S_{j}=\Phi$   for    $i\neq j$  , we have  

$$
\mu\left(\bigcup S_{n}\right)=\bigcup_{n}\mu(S_{n})\quad(\sigma\mathrm{-diffusivity})
$$  

and a requirement for continuity at if a sequence    $S_{1}\supseteq S_{2}\supseteq S_{3}\supseteq$  · · ·  tends to the empty set, then  $\mu(S_{n})\to0$   → 0. All this abstract theory can be summarised by saying that a numerical probability is a measure  $\mu$   on a Boolean  $\sigma$  -algebra    $\Im$  of subsets of a set  $\Omega$  , such that    $\mu(\Omega)=1$   (Halmos, 1950).  

We rarely work with probability functions in this form, and we usually see them deﬁned slightly differently    $P(.)$   is a positive real-valued function on an event space, where    $E_{0}$   is the empty event,    $E_{1}$   the universal event, and then  

$$
P(E_{0})=0\;\mathrm{and}\;P(E_{1})=1,
$$  

A conditional probability is then deﬁned by  

$$
P(E\,|\,F)={\frac{P(E\cap F)}{P(F)}}{\mathrm{~provided~that~}}P(F)\neq0.
$$  

One can then transform this latter equation into Bayes’ Theorem, which is  

$$
P(E\,|\,F)={\frac{P(F\,|\,E)P(E)}{P(F)}}.
$$  

Because of a famous corollary to the Stone Representation Theorem: every Boolean algebra is isomorphic to a ﬁeld of sets (Halmos, 1963), it is possible to substitute propositional variables for events. Thus we can deﬁne probability as a real-valued function  $P$   on an algebra of propositions satisfying the following axioms:  

Conditional probability and Bayes’ Theorem can then be re-expressed in terms of propositions instead of subsets.  

# Quantum probability  

When it comes to deﬁning a probability function for quantum mechanics the situation is somewhat different. There is an excellent paper by Jauch (1976) in Suppes (1976) that shows how to deﬁne probability and random variables for quantum mechanics, with deﬁnitions motivated by the classical deﬁnitions.  

In essence the powerset of subsets of a set of outcomes (the sample space) which forms a Boolean lattice is replaced by a non-Boolean lattice on which a probability measure is deﬁned thus.  

Let  $L$   be the lattice of elementary events. Then a probability measure on    $L$  , a function    $\mu\colon L\to[0,\,1]$  , is deﬁned on  $L$   with values in [0, 1] satisfying the following conditions:  

$\begin{array}{l}{{\displaystyle\sum\mu(a_{i})=\mu(\cup a_{i}),~~~~\mathrm{for}\;a_{i}\in L,\quad i=1,2,\ldots,\quad a_{i}\,\bot\,a_{j},\mathrm{~w~i~t~.~}}}\\ {{\displaystyle\mu(\Phi)=0,\quad\mu(\mathrm{I})=1,\mathrm{~where~}\Phi\mathrm{~is~the~smallest~and~I~is~the~bar}.}}\end{array}$   when    $i\neq j$  ;  is the smallest and I is the largest element in  $L$  ;  

if    $\mu(a)=\mu(b)=1$   then    $\mu(a\cap b)=1$  .  

This deﬁnition is made more concrete if the lattice elements are interpreted as the subspaces of a Hilbert space    $\mathbf{H}$  . It is a well known result that this    $\wp({\bf H})$  , the lattice of closed subspaces of a complex Hilbert space, is a non-Boolean lattice of a special kind (see, for example, Birkhoff and Von Neumann, 1936, or Beltrametti and Cassinelli, 1981).  

A less abstract deﬁnition of the probability measure can now be given in terms of the closed subspaces of    $\mathbf{H}$  . Let    $\varphi$   be any normalised vector in the Hilbert space    $\mathbf{H}$  , then a probability measure    $\mu$   on the set of subspaces  $L=\wp({\bf H})$   is deﬁned as follows:  

$$
\begin{array}{r}{\mu_{\varphi}(\Phi)=0,}\\ {\mu_{\varphi}(\mathbf{H})=1.}\end{array}
$$  

For subspaces  $L_{i}$   and  $L_{j}$  ,  $\mu_{\varphi}(L_{i}\oplus L_{j})=\mu_{\phi}(L_{i})+\mu_{\varphi}(L_{j})$   provided  $L_{i}\cap L_{j}=\Phi$  . Observe that the measure    $\mu$   is deﬁned with respect to a particular vector    $\varphi$  , a different measure for different vectors. The symbol    $\oplus$  is used to indicate the linear span of two subspaces, which in the classical axioms would have been the union of two sets. For a more general form of the probability axioms, interested readers should consult Parthasarathy (1992).  

A concrete realisation of such a probability measure can be given. To do this we need to deﬁne brieﬂy  trace  and  density operator  (see Chapter 6).  

$$
\operatorname{tr}(\mathbf{A})=\sum_{i}\langle\varphi_{i}|\mathbf{A}|\varphi_{i}\rangle,{\mathrm{where~}}\langle\varphi|\mathbf{A}|\varphi\rangle>0\,\,\,\forall\varphi\in\mathbf{H},
$$  

The trace  $\mathrm{tr}(.)$   has the following properties if the traces are ﬁnite and  $\alpha$   a scalar:  

$$
\begin{array}{r l}&{\qquad\mathrm{tr}(\alpha\mathbf{A})=\alpha\mathrm{tr}(\mathbf{A}),}\\ &{\qquad\mathrm{tr}(\mathbf{A}+\mathbf{B})=\mathrm{tr}(\mathbf{A})+\mathrm{tr}(\mathbf{B}).}\end{array}
$$  

Now a  density operator    $\mathbf{D}$   is such that    $\langle\varphi\vert{\bf D}\vert\varphi\rangle\,>\,0\;\forall\;\varphi\,\in{\bf H}$   and   $\operatorname{tr}(\mathbf{D})=1$  . So, for example, every projection operator onto a 1-dimensional subspace is a density operator, and its trace is unity. Moreover, any linear combination  $\textstyle\sum_{i}\alpha\mathbf{P}_{i}$   of such  rojectors  $\mathbf{P}_{i}$  here    $\textstyle\sum_{i}\alpha=1$   = s a density operator. If we now deﬁne for any projector  P  $\mathbf{P}_{L}$   onto subspace  L  the quantity   $\ensuremath{\mathbf{tr}}(\ensuremath{\mathbf{D}}\ensuremath{\mathbf{P}}_{L})$   for a density operator  D , we ﬁnd that it is a probability measure on the subspaces  $L$  :  $\mu(L)=\operatorname{tr}(\mathbf Ḋ \mathbf Ḋ P Ḍ _{L})$  , conforming to the axioms deﬁned above. Signiﬁcantly, the reverse is true as well, that is that given a probability measure on the closed sub- spaces of a Hilbert space  $\mathbf{H}$  , then there exists a density operator that ‘computes’ the probability for each subspace (Gleason, 1957).  

Let us do a simple example. Let  $\mathbf{D}=|\varphi\rangle\langle\varphi|$   and   $\mathbf{P}_{\psi}=\vert\psi\rangle\langle\psi\vert$  . Then  

$$
\begin{array}{r l}&{\mathrm{tr}(\mathbf Ḋ \mathbf Ḋ \mathbf Ḋ P Ḍ Ḍ _{\psi})=\mathrm{tr}(|\varphi\rangle\langle\varphi\|\psi\rangle\langle\psi|)=\mathrm{tr}(|\varphi\rangle\langle\varphi\mid\psi\rangle\langle\psi|)}\\ &{\phantom{\mathrm{tr}(\mathbf Ḋ \psi Ḍ _{\psi})=}=\langle\varphi\mid\psi\rangle\mathrm{tr}(|\varphi\rangle\langle\psi|)=\langle\varphi\mid\psi\rangle\langle\psi\mid\varphi\rangle=|\langle\varphi\mid\psi\rangle|^{2},}\end{array}
$$  

which by now is a familiar result showing that the probability of getting a yes answer to the question  $\mathbf{P}_{\psi}$   when the system is in state    $\mathbf{D}$   is    $|\langle\varphi\mid\psi\rangle|^{2}$    (refer to Appendix   $\mathrm{II}$   for more details).  

# Further reading  

Williams (2001), apart from being an excellent book on probability theory, con- tains a comprehensive chapter on quantum probability. For the real enthusiast we recommend Pitowsky (1989), which describes and explains many results in quantum probability in great detail and makes appropriate connections with quantum logic.  

Accardi, L. and A. Fedullo (1982). ‘On the statistical meaning of complex numbers in quantum mechanics.’  Lettere al nuovo cimento  34 (7): 161–172. Gives a technical acount of the necessity for using complex rather than real Hilbert spaces in quantum mechanics. There is no equivalent argument for IR (yet). Aerts, D. (1999). ‘Foundations of quantum physics: a general realistic and operational approach.’  International Journal of Theoretical Physics  38 (1): 289–358. This is a careful statement of the basic concepts of quantum mechanics. Most of it is done from ﬁrst principles and the paper is almost self-contained. The foundations are presented from an operational point of view. Aerts, D., T. Durt, A. A. Grib, B. van Bogaert and R. R. Zupatrin (1993). ‘Quantum structures in macroscopic reality.’  International Journal of Theoretical Physics 32 (3): 489–498. They construct an artiﬁcial, macroscopic device that has quantum properties. The corresponding lattic is non-Boolean. This example may help in grasping non-Boolean lattices in the abstract. Albert, D. Z. (1994).  Quantum Mechanics and Experience , Harvard University Press. This is one of the best elementary introductions to quantum mechanics, written with precision and very clear. The examples are very good and presented with considerable ﬂair. It uses the Dirac notation and thus provides a good entry point for that too, although the mathematical basis for it is never explained. Albert, D. and B. Loewer (1988). ‘Interpreting the many worlds interpretation.’  Synthese 77 : 195–213. The many worlds interpretation is worth considering as a possible model for interpreting the geometry of information retrieval. Albert and Loewer give a clear and concise introduction to the many world approach as pioneered by Everett (DeWitt and Graham, 1973). Amari, S.-i. and H. Nagaoka (2000).  Methods of Information Geometry , Oxford University Press. This one is not for the faint hearted. It covers the connection between geometric structures and probability distribution, but in a very abstract way. Chapter 7 gives an account of ‘information geometry’ for quantum systems. It deﬁnes a divergence measure for quantum systems equivalent to the Kullback divergence. For those interested in quantum information this may prove of interest. Amati, G. and C. J. van Rijsbergen (1998). ‘Semantic information retrieval.’ In Information Retrieval: Uncertainty and Logics , F. Crestani, M. Lalmas and  

C. J. van Rijsbergen (eds.). Kluwer, pp. 189–219. Contains a useful discussion on various formal notions of information content. Arveson, W. (2000).  A short course on spectral theory . Springer Verlag. Alternative to Halmos (1951). A fairly dense treatment. Auletta, G. (2000).  Foundations and Interpretation of Quantum Mechanics; in the Light of a Critical-Historical Analysis of the Problem and of a Synthesis of the Results . World Scientiﬁc. This book is encyclopedic in scope. It is huge – 981 pages long and contains a large bibliography with a rough guide as to where each entry is relevant, and the book is well indexed. One can ﬁnd a discussion of almost any aspect of the interpretation of QM. The mathematics is generally given in its full glory. An excellent source reference. The classics are well cited. Auyang, S. Y. (1995).  How is Quantum Field Theory Possible?  Oxford University Press. Here one will ﬁnd a simple and clear introduction to the basics of quantum mechan- ics. The mathematics is kept to a minimum. Bacciagaluppi, G. (1993). ‘Critique of Putnam’s quantum logic.’  International Journal of Theoretical Physics  32 (10): 1835–1846. Relevant to Putnam (1975). Baeza-Yates, R. and B. Ribeiro-Neto (1999).  Modern Information Retrieval , Addison Wesley.A solid introduction to information retrieval emphasising the computational aspects. Contains an interesting and substantial chapter on modelling. Contains a bibliography of 852 references, also has a useful glossary. Baggott, J. (1997).  The Meaning of Quantum Theory , Oxford University Press. Fairly leisurely introduction to quantum mechanics. Uses physical intuition to motivate the Hilbert space mathematics. Nice examples from physics, and a good section on the Bohr–Einstein debate in terms of their thought experiment ‘the photon box experiment’. It nicely avoids mathematical complications. Barrett, J. A. (1999).  The Quantum Mechanics of Minds and Worlds , Oxford University Press. This book is for the philosophically minded. It concentrates on an elaboration of the many-worlds interpretation invented by Everett, and ﬁrst presented in his doctoral dissertation in 1957. Barwise, J. and J. Seligman (1997).  Information Flow: The Logic of Distributed Systems , Cambridge University Press. Barwise has been responsible for a number of inter- esting developments in logic. In particular, starting with the early work of Dretske, he developed together with Perry an approach to situation theory based on notions of information, channels and information ﬂow. What is interesting about this book is that in the last chapter of the book, it relates their work to quantum logic. For this it used the theory of manuals developed for quantum logic, which is itself explained in detail in Cohen (1989). Belew, R. (2000).  Finding Out About: a Cognitive Perspective on Search Engine Technol- ogy and the WWW . Cambridge University Press. Currently one of the best textbooks on IR in print. It does not shy away from using mathematics. It contains a good section introducing the vector space model pioneered by Salton (1968) which is useful material as background to the Hilbert space approach adopted in GIR. The chapter on mathematical foundations will also come in handy and is a useful ref- erence for many of the mathematical techniques used in IR. There is a CD insert on which one will ﬁnd, among other useful things, a complete electronic version of Van Rijsbergen (1979a).  

Bell, J. S. (1993).  Speakable and Unspeakable in Quantum Mechanics , Cambridge University Press. A collection of previously published papers by the famous Bell, responsible for the Bell inequalities. Several papers deal with hidden variable the- ories. Of course it was Bell who spotted a mistake in Von Neumann’s original proof that there was no hidden-variable theory for quantum mechanics. It contains a critique of Everett’s many-worlds interpretation of quantum mechanics. It also contains ‘Beables for quantum ﬁeld theory’. Beltrametti, E. G. and G. Cassinelli (1977). ‘On state transformation induced by yes– no experiments, in the context of quantum logic.’  Journal of Philosophical Logic 6 : 369–379. The nature of the conditional in logic as presented by Stalnaker and Hardegree can be shown to play a special role in quantum logic. Here we have a discussion of how YES–NO experiments can be useful in giving meaning to such a conditional. — (1981).  The Logic of Quantum Mechanics . Addison-Wesley Publishing Company. This is a seminal book, a source book for many authors writing on logic and probability theory in quantum mechanics. Most of the mathematical results are derived from ﬁrst principles. Chapter 9 is a good summary of the Hilbert space formulation which serves as an introduction to Part II: one of the best introductions to the mathematical structures for quantum logics. It is well written. Chapter 20 is a very good brief introduction to quantum logic. Beltrametti, E. G. and B. C. van Fraassen, eds. (1981).  Current Issues in Quantum Logic . Plenum Press. This volume collects together a number of papers by inﬂuential thinkers on quantum logic. Many of the papers are written as if from ﬁrst principles. It constitutes an excellent companion volume to Beltrametti and Cassinelli (1981) and Van Fraassen (1991). Many of the authors cited in this bibliography have a paper in this volume, for example, Aerts, Bub, Hardegree, Hughes and Mittelstaedt. A good place to start one’s reading on quantum logic. Bigelow, J. C. (1976). ‘Possible worlds foundations for probability.’  Journal of Philosophical Logic  5 : 299–320. Based on the notion of similarity heavily used by David Lewis to deﬁne a semantics for counterfactuals; Bigelow uses it to deﬁne probability. This is good background reading for Van Rijsbergen (1986). — (1977). ‘Semantics of probability.’  Synthese  36 : 459–472. A useful follow-on paper to Bigelow (1976). Birkhoff, G. and S. MacLane (1957).  A Survey of Modern Algebra . The Macmillan Company. One of the classic textbooks on algebra by two famous and ﬁrst rate mathematicians. This is the Birkhoff that collaborated with John von Neumann on the logic of quantum mechanics and in 1936 published one of the ﬁrst papers ever on the subject. Most elementary results in linear algebra can be found in the text. There is a nice chapter on the algebra of classes which also introduces partial orderings and lattices. Birkhoff, G. and J. von Neumann (1936). ‘The logic of quantum mechanics.’  Annals of Mathematics  37 : 823–843. Reprinted in Hooker (1975), this is where it all started! ‘The object of the present paper is to discover what logical structure one may hope to ﬁnd in physical theories which, like quantum mechanics, do not conform to classical logic. Our main conclusion, based on admittedly heuristic arguments, is that one can reasonable expect to ﬁnd a calculus of propositions which is formally  

indistinguishable from the calculus of linear subspaces with respect to set products, linear sums, and orthogonal complements – and resembles the usual calculus of propositions with respect to and, or, and not.’ Ever since this seminal work there  

has been a steady output of papers and ideas on how to make sense of it. Blair, D. C. (1990).  Language and Representation in Information Retrieval . Elsevier. A thoughtful book on the philosophical foundations of IR, it contains elegant descrip- tions of some of the early formal models for IR. Enjoyable to read. Blum, K. (1981). ‘Density matrix theory and applications.’ In  Physics of Atoms and Molecules , P. G. Burke (ed.) Plenum Press, pp. 1–62. It is difﬁcult to ﬁnd an elementary introduction to density matrices. This is one, although it is mixed up with applications to atomic physics. Nevertheless Chapter 2, which is on general density matrix theory, is a good self-contained introduction which uses the Dirac notation throughout. Borland, P. (2000).  Evaluation of Interactive Information Retrieval Systems . Abo Akademi University. Here one will ﬁnd a methodology for the evaluation of IR systems that goes beyond the now standard ‘Cranﬁeld paradigm’. There is a good discussion of the concept of relevance and the book concentrates on retrieval as an interactive process. The framework presented in GIR should be able to present and formalise such a process. Bouwmeester, D., A. Ekert and A. Zeiliager, eds. (2001).  The Physics of Quantum Information , Springer-Verlag. Although not about quantum computation per se, there are some interesting connections to be made. This collection of papers covers quantum cryptography, teleportation and computation. The editors are experts in their ﬁeld and have gone to some trouble to make the material accessible to the non-expert. Bruza, P. D. (1993).  Stratiﬁed Information Disclosure: a Synthesis between Hypermedia and Information Retrieval . Katholieke University Nijmegen. A good example of the use of non-standard logic in information retrieval. Bub, J. (1977). ‘Von Neumann’s projection postulate as a probability condition aliz ation rule in quantum mechanics.’  Journal of Philosophical Logic  6 : 381–390. The title says it all. The Von Neumann projection postulate has been a matter of debate ever since he formulated it; it was generalised by L¨ uders in 1951. Bub gives a nice introduction to it in this paper. The interpretation as a conditional is ation rule is important since it may be a useful way of interpreting the postulate in IR. Van Fraassen (1991, p. 175) relates it to  Jeffrey  conditional is ation (Jeffrey,1983).

 — (1982). ‘Quantum logic, conditional probability, and interference.’  Philosophy of Science  49 : 402–421. Good commentary on Friedman and Putnam (1978).

 — (1997).  Interpreting the Quantum World , Cambridge University Press. Bub has been publishing on the interpretation of quantum mechanics for many years. One of his major interests has been the projection postulates, and their interpretation as a collapse of the wave function. The ﬁrst two chapters of the book are well worth reading, introducing many of the main concepts in QM. The mathematical appendix is an excellent introduction to Hilbert space machinery. Busch, P., M. Grabowski and P. J. Lanti (1997).  Operational Quantum Physics , Springer- Verlag. There is a way of presenting quantum theory from the point of view of positive operator valued measures, which is precisely what this book does in great detail.  

Butterﬁeld, J. and J. Melia (1993). ‘A Galois connection approach to superposition and inaccessibility.’  International Journal of Theoretical Physics  32 (12): 2305–2321. In Chapter 2 on inverted ﬁles and natural kinds, we make use of a Galois connection. In this paper quantum logic is discussed in terms of a Galois connection. A fairly technical paper, most proofs are omitted. Campbell, I. and C. J. van Rijsbergen (1996).  The Ostensive Model of Developing Information Needs . CoLIS 2, Second International Conference on Conceptions of Library and Information Science: Integration in Perspective, Copenhagen, The Royal School of Librarianship. A description of an IR model to which the theory presented in GIR will be applied. It is the companion paper to Van Rijsbergen (1996). Carnap, R. (1977).  Two Essays on Entropy , University of California Press. For many years these essays remained unpublished. An introduction by Abner Shimony explains why. Carnap’s view on the nature of information diverged signiﬁcantly from that of Von Neumann’s. John Von Neumann maintained that there was one single physical concept of information, whereas Carnap, in line with his view of probability, thought this was not adequate. Perhaps these essays should be read in conjunction with Cox (1961) and Jaynes (2003). Cartwright, N. (1999).  How the Laws of Physics Lie , Clarendon Press. Essay 9 of this book contains a good introduction to what has become known in QM as ‘The Measurement Problem’: the paradox of the time evolution of the wave function versus the collapse of the wave function. A clear and elementary account. Casti, J. L. (2000).  Five More Golden Rules: Knots, Codes, Chaos, and Other Great Theories of Twentieth Century Mathematics . Wiley. Contains a semi-popular intro- duction to functional analysis. The section on quantum mechanics is especially worth reading. Cohen, D. W. (1989).  An Introduction to Hilbert Space and Quantum Logic , Springer- Verlag.Good introduction to quantum logic s,explaining the necessary Hilbert space as needed. It gives a useful proof of Gleason’s Theorem, well actually almost, as it leaves it to be proved as a number of guided projects. Here the reader will also ﬁnd a good introduction to ‘manuals’ with nice illustrative examples. Note in particular the ‘ﬁreﬂy in a box’ example. Cohen-Tannoudji, C., B. Diu and F. Lalo¨ e (1977).  Quantum Mechanics . Wiley. A stan- dard and popular textbook on QM. It is one of the few that has a comprehensive section on density operators. Collatz, L. (1966).  Functional Analysis and Numerical Mathematics , Academic Press. Contrary to what the title may lead one to believe, almost half of this book is devoted to a very clear, self-contained, introduction to functional analysis. For example, it is has a thorough introduction to operators in Hilbert space. Colodny, R. G., ed. (1972).  Paradigms and Paradoxes. The Philosophical Challenge of the Quantum Domain , University of Pittsburgh Press. The lion’s share of this book is devoted to a lengthy paper by C. A. Hooker on quantum reality. However, the papers by Arthur Fine and David Finkelstein on conceptual issues to do with probability and logic in QM are well worth reading. Cooke, R., M. Keane and W. Moran (1985). ‘An Elementary Proof of Gleason’s Theorem.’  Mathematical Proceedings of the Cambridge Philosophical Society 98 : 117–128. Gleason’s Theorem is central to the mathematical approach in GIR.  

Gleason published his important result in 1957. The proof was quite difﬁcult and eventually an elementary proof was given by Cooke  et al . in 1985. Hughes (1989) has annotated the proof in an Appendix to his book. Richman and Bridges (1999) give a constructive prooof. The theorem is of great importance in QM and hence is derived in a number of standard texts on quantum theory, for example Varadarajan (1985), Parthasarathy (1992) and Jordan (1969).  

Cox, R. T. (1961).  The Algebra of Probable Inference . The Johns Hopkins Press. This is a much cited and quoted book on the foundations of probability. For example, in his recent book on Probability Theory, Jaynes (2003) quotes results from Cox. The book has sections on probability, entropy and expectation. It was much inﬂuenced by Keynes’  A Treatise on Probability  (1929), another good read.  

Crestani, F., M. Lalmas and C. J. van Rijsbergen, eds. (1998).  Information Retrieval: Uncertainty and Logics: Advanced Models for the Representation and Retrieval of Information . Kluwer. After the publication of Van Rijsbergen (1986), which is reprinted here, a number of researchers took up the challenge to deﬁne and develop appropriate logics for information retrieval. Here we have a number of research papers showing the progress that was made in this ﬁeld, that is now often called the ‘Logical model for IR’. The papers trace developments from around 1986 to roughly 1998. The use of the Stalnaker conditional (Stalnaker, 1970) for IR was ﬁrst proposed in the 1986 paper discussed in some detail in Chapter 5 in GIR.  

Crestani, F. and C. J. van Rijsbergen (1995). ‘Information retrieval by logical imaging.’ Journal of Documentation  51 : 1–15. A detailed account of how to use imaging (Lewis, 1976) in IR. Croft, W. B. (1978).  Organizing and Searching Large Files of Document Descriptions . Cambridge, Computer Laboratory , Cambridge University. A detailed evaluation of document clustering based on the single link hierarchical classiﬁcation method. Croft, W. B. and J. Lafferty, eds. (2003).  Language Modeling for Information Retrieval . Kluwer. The ﬁrst book on language modelling. It contains excellent introductory papers by Lafferty and Xhia, as well as by Lavrenk and Croft. Dalla Chiara, M. L. (1986). ‘Quantum logic.’ In  Handbook of Philosophical Logic , D. Gabbay and F. Guenthner (eds.). Reidel Publishing Company III, pp. 427–469. A useful summary of quantum logic given by a logician. — (1993). ‘Empirical Logics.’  International Journal of Theoretical Physics  32 (10): 1735–1746. A logician looks at quantum logics. The result is a fairly sceptical view not too dissimilar from Gibbins (1987). Davey, B. A. and H. A. Priestley (1990).  Introduction to Lattices and Order , Cambridge University Press. Here you will ﬁnd all you will ever need to know about lattices. The ﬁnal chapter on formal concept analysis introduces the Galois Connection. De Broglie, L. (1960).  Non-Linear Wave Mechanics. A Causal Interpretation , Elsevier Publishing Company. A classic book. Mainly of historical interest now. De Broglie is credited with being the ﬁrst to work out the implications of    $l=h/m\nu$   (page 6), the now famous connection between wavelength and momentum,  h  is Planck’s constant. De Finetti, B. (1974).  Theory of Probability . Wiley. A masterpiece by the master of the subjectivist school of probability. Even though it has been written from the point of view of a subjectivist, it is a rigorous complete account of the basics of probability  

theory. He discusses fundamental notions like independence in great depth. The book has considerable philosophical depth; De Finetti does not shy away from  

of the subject, following the argument is always rewarding. Debnath, L. and P. Mikusinski (1999).  Introduction to Hilbert spaces with Applica- tions , Academic Press. A standard textbook on Hilbert spaces. Many of the impor- tant results are presented and proved here. It treats QM as one of a number of applications. Deerwester, S., S. T. Dumais, G. F. W. Furnas, T. K. Landauer and R. Harsman (1990). ‘Indexing by Latent Semantic Analysis.’  Journal of the American Society for Infor- mation Science  4 : 391–407. This is one of the earliest papers on latent semantic indexing. Despite many papers on the subject since the publication of this one, it is still worth reading. It presents the basics ideas in a simple and clear way. It is still frequently cited. D’Espagnat, B. (1976).  Conceptual Foundations of Quantum Mechanics , W. A. Benjamin, Inc. Advanced Book Program. This must be one of the very ﬁrst books on the conceptual foundations of QM. It takes the approach that a state vector represents an ensemble of identically prepared quantum systems. It gives a very complete account of the density matrix formalism in Chapter 6, but beware of some trivial typos. It is outstanding for its ability to express and explain in words all the important fundamental concepts in QM. It also gives accurate mathematical explanations. This book is worth studying in detail. — (1990).  Reality and the Physicist. Knowledge, Duration and the Quantum World , Cambridge University Press. This is a more philosophical and leisurely treatment of some of the material covered in d’Estaganat (1976). Deutsch, D. (1997).  The Fabric of Reality , Allen Lane. The Penguin Press. This is a very personal account of the importance of quantum theory for philosophy and computation. David Deutsch was one of the early scientists to lay the foundations for quantum computation. His early papers sparked much research and debate about the nature of computation. This book is written entirely without recourse to rigorous mathematical argument. It contains copious references to Turing’s ideas on computability. Deutsch, F. (2001).  Best Approximation in Inner Product Spaces , Springer. Inner prod- ucts play an important role in the development of quantum theory. Here one will ﬁnd inner products discussed in all their generality. Many other algebraic results with a geometric ﬂavour are presented here. DeWitt, B. S. and N. Graham, eds. (1973).  The Many-Worlds Interpretation of Quantum Mechanics . Princeton Series in Physics, Princeton University Press. Here are col- lected together a number of papers about the many-worlds interpretation, including a copy of Everett’s original dissertation on the subject, entitled, ‘The Theory of the Universal Wave Function’. This latter paper is relatively easy to read. It makes frequent use of statistical information theory in a way not unknown to information retrievalists. Dirac, P. A. M. (1958).  The Principles of Quantum Mechanics , Oxford University Press. One of the great books of quantum mechanics. The ﬁrst one hundred pages are still worth reading as an introduction to QM. Dirac motivates the introduction of the mathematics. In particular he defends the use of the Dirac notation. He  

takes as one of his guiding principles the superposition of states, and takes some time to defend his reason. This book is still full of insights, well worth spending  

time on. — (1978). ‘The mathematical foundations of quantum theory.’ In  The Mathematical Foundations of Quantum Theory . A. R. Marlow (ed.). Academic Press: 1–8. This paper is by way of a preface to the edited volume by Marlow. It contains a late statement of the master’s personal philosophy concerning foundational research. The quote: ‘Any physical or philosophical ideas that one has must be adjusted to ﬁt the mathematics.’ is taken from this paper. Dominich, S. (2001).  Mathematical Foundations of Information Retrieval , Kluwer Academic Publishers. A very mathematical approach to information retrieval. Dowty, D., R. Wall and S. Peters (1981).  Introduction to Montague Semantics . Reidel. Still one of the best introductions to Montague Semantics. Is is extremely well written. If one wishes to read Montague’s original writings this is a good place to start. Einstein, A., B. Podolsky and N. Rosen (1935). Can quantum mechanical descriptions of physical reality be considered complete?  Physical Review  47 : 777–780 Engesser, K. and D. M. Gabbay (2002). ‘Quantum Logic, Hilbert Space, Revision Theory.’  Artiﬁcial Intelligence  136 : 61–100. This is a look at quantum logic by logicians with a background in computer science. It has a little to say about prob- ability measures on the subspaces of a Hilbert space. Fairthorne, R. A. (1958). ‘Automatic Retrieval of Recorded Information.’  The Com- puter Journal  1 : 36–41. Fairthorne’s paper, reprinted in Fairthorne (1961), is now mainly of historical interest. The opening section of the paper throws some light on the history of IR; Vannevar Bush is usually cited as the source of many of the early ideas in IR, but Fairthorne gives details about much earlier original work. — (1961).  Towards Information Retrieval , Butterworths. One of the very ﬁrst books on information retrieval, it is of particular interest because Fairthorne was an early proponent of the use of Brouwerian logics in IR. A useful summary of this approach is given in Salton (1968). Fano, G. (1971).  Mathematical Methods of Quantum Mechanics , McGraw-Hill Book Company. A ﬁne introduction to the requisite mathematics for QM. It is clearly geared to QM although the illustrations are mostly independent of QM. It contains a useful explanation of the Dirac notation (section 2.5). Its section (5.8) on the spectral decomposition of a self-adjoint operator is important and worth reading in detail. Feller, W. (1957).  An Introduction to Probability Theory and Its Applications . One of the classic mathematical introductions to probability theory. Feynman, R. P. (1987). ‘Negative probability.’ In  Quantum Implications , B. J. Hiley and F. D. Peat (eds.) Routledge & Kegan Paul, pp. 235–248. This paper is of interest because it represents an example of using a ‘non-standard’ model for probability theory, to be compared with using complex numbers instead of real numbers. It illustrates how intermediate steps in analysis may fail to have simple na¨ ıve interpretations. Feynman, R. P., R. B. Leiguton and M. Sands (1965).  The Feynman Lectures on physics , vol. III, Addison-Wesley.  

Finch, P. D. (1975). ‘On the structure of quantum logic.’ In  The Logico-Algebraic Approach to Quantum Mechanics , Vol I., C. A. Hooker (ed.) pp. 415–425. An account of quantum logic without using the usual physical motivation. Fine, A. (1996).  The Shaky Game. Einstein Realism and the Quantum Theory , The University of Chicago Press. Einstein never believed in the completeness of quan- tum mechanics. He did not accept that probability had an irreducible role in fun- damental physics. He famously coined the sentence ‘God does not play dice’. Here we have an elaboration of Einstein’s position. This book should be seen as a contribution to the philosophy and history of QM. Finkbeiner, D. T. (1960).  Matrices and Linear Transformations , W. H. Freeman and Company. A standard textbook on linear algebra. It is comparable to Hal mos(1958), and it covers similar material. It uses a postﬁx notation for operator application which can be awkward. Nevertheless it is clearly written, even though with less ﬂair than Halmos. It contains numerous good examples and exercises. Fisher, R. A. (1922).  On the Dominance Ratio . Royal Society of Edinburgh. This paper is referred to by Wootters (1980a). The claim is that it is one of the ﬁrst papers to describe a link between probability and geometry for vector spaces. It is not easy to establish that. The reference is included for the sake of completeness. Frakes, W. B. and R. Baeza-Yates, eds. (1992).  Information Retrieval – Data Structures & Algorithms , Prentice Hall. A good collection of IR papers covering topics such as ﬁle structures, NLP algorithms, ranking and clustering algorithms. Good source for technical details of well-known algorithms. Friedman, A. (1982).  Foundations of Modern Analysis , Dover Publications, Inc. The ﬁrst chapter contains a good introduction to measure theory. Friedman, M. and H. Putnam (1978). ‘Quantum logic, conditional probability, and interference.’  Dialectica  32 (3–4): 305–315. The authors wrote this now inﬂuential paper, claiming ‘The quantum logical interpretation of quantum mechanics gives an explanation of interference that the Copenhagen interpretation cannot supply.’ It all began with Putnam’s original 1968 ‘Is logic empirical?’, subsequently updated and published as Putnam (1975). It has been a good source for debate ever since, for example, Gibbins (1981) Putnam (1981) and Bacciagaluppi (1993), to name but a few papers. Ganter, B. and R. Wille (1999).  Formal Concept Analysis – Mathematical Foundations , Springer-Verlag. This is a useful reference for the material in Chapter 2 of this book. Garden, R. W. (1984).  Modern Logic and Quantum Mechanics , Adam Hilger Ltd., Bristol. One could do a lot worse than start with this as a ﬁrst attempt at under- standing the role of logic in classical and quantum mechanics. Logic is ﬁrst used in classical mechanics, which motivates its use in quantum mechanics. The pace is very gentle. The book ﬁnishes with Von Neumann’s quantum logic as ﬁrst outlined in the paper by Birkhoff and Von Neumann (1936). Gibbins, P. (1981). ‘Putnam on the Two-Slit Experiment.’  Erkenntnis  16 : 235–241. A critique of Putnam’s 1969 paper (Putnam, 1975). — (1987).  Particles and Paradoxes: the Limits of Quantum Logic , Cambridge University Press. An outstanding informal introduction to the philosophy and interpretations of QM. It has a unusual Chapter 9, which gives a natural deduction formulation of quantum logic. Gibbins is quite critical of the work on quantum logic and in the ﬁnal chapter he summarises some of his criticisms.  

Gillespie, D. T. (1976).  A Quantum Mechanics Primer. An Elementary Introduction to the Formal Theory of Non-relativistic Quantum Mechanics , International Textbook Co. Ltd. A modest introduction to QM. Avoids the use of Dirac notation. It was an Open University Set Book and is clearly written. Gleason, A. M. (1957). ‘Measures on the closed subspaces of a Hilbert space.’  Journal of Mathematics and Mechanics  6 : 885–893. This is the original Gleason paper containing the theorem frequently referred to in GIR. Simpler versions are to found in Cooke  et al . (1985), and Hughes (1989). — (1975). ‘Measures of the closed subspaces of a Hilbert space.’ In  The Logico- Algebraic Approach to Quantum Mechanics , C. A. Hooker (ed.) pp. 123–133. This is a reprint of Gleason’s original paper published in 1957. Goffman, W. (1964). ‘On relevance as a measure.’  Infomation Storage and Retrieval  2 : 201–203. Goffman was one of the early dissenters from the standard view of the concept of relevance. Goldblatt, R. (1993).  Mathematics of Modality , CSLI Publications. The material on orthologic and orthomodular structures is relevant. The treatment is dense and really aimed at logicians. Golub, G. H. and C. F. van Loan (1996).  Matrix Computations , The Johns Hopkins University Press. A standard textbook on matrix computation. Good, I. J. (1950).  Probability and the weighing of evidence . Charles Grifﬁn & Company Limited. Mainly of historical interest now, but contains a short classiﬁcation of theories of probability. Greechie, R. J. and S. P. Gudder (1973). ‘Quantum logics.’ In  Contemporary Research in the Foundations and Philosophy of Quantum Theory , C. A. Hooker (ed.), D. Reidel Publishing Company, pp. 143–173. A wonderfully clear account of the mathemat- ical tools neeeded for the study of axiomatic quantum mechanics. Greenstein, G. and A. G. Zajonc (1997).  The Quantum Challenge. Modern Research on the Foundations of Quantum Mechanics , Jones and Bartlett. A relatively short and thorough introduction to QM. The emphasis is on conceptual issues, mathematics is kept to a minimum. Examples are taken from physics. Gribbin, J. (2002).  Q is for Quantum: Particle Physics from A to Z . Phoenix Press. A popular glossary for particle physics, but contains a large number of entries for QM. Grifﬁths, R. B. (2002).  Consistent Quantum Theory , Cambridge University Press. A superb modern introduction to quantum theory. The important mathematics is introduced very clearly. Toy examples are used to avoid complexities. It contains a thorough treatment of histories in QM, which although not used in this book, could easily be adapted for IR purposes. Tensor products are explained. Some the paradoxical issues in logic for QM are addressed. This is possibly one of the best modern introductions to QM for those interested in applying it outside physics. Grover, L. K. (1997). ‘Quantum mechanics helps in searching for a needle in a haystack.’ Physical Review Letters  79 (2): 325–328. The famous paper on ‘ﬁnding a needle in a haystack’ by using quantum computation and thereby speeding up the search compared with what is achievable on a computer with a Von Neumann architecture.  

Gruska, J. (1999).  Quantum Computing , McGraw Hill. For the sake of completeness a number of books on quantum computation are included. This is one of them. It contains a brief introduction to the fundamentals of Hilbert space; useful for someone in a hurry to grasp the gist of it. Halmos, P. R. (1950).  Measure Theory . Van Nostrand Reinhold Company. A classic introduction to the subject. It is written with the usual Halmos upbeat style. It has an excellent chapter on probability from the point of view of measure theory.

 — (1951).  Introduction to Hilbert Space and the Theory of Spectral Multiplicity , Chelsea Publishing Company. This is a very lively introduction to Hilbert space and explains the details behind spectral measures. This book should be read and consulted in conjunction with Halmos (1958). Even though it is very high powered it is written in an easy style, and it should be compared with Arveson (2002) and Retherford (1993); both these are more recent introductions to spectral theory.

 — (1958).  Finite-Dimensional Vector Spaces , D. van Nostrand Company, Inc. This is one of the best books on ﬁnite-dimensional vector spaces, even though it was published so many years ago. It is written in a deceptively simple and colloquial style. It is nicely divided into ‘bite size’ chunks and probably you will learn more than you ever would want to know about vector spaces. It is also a good introduction to Halmos’s much more sophisticated and harder book on Hilbert spaces.

 — (1963).  Lectures on Boolean Algebra . D. Van Nostrand Company. All you might ever want to know about Boolean Algebra can be found here. Contains a proof of the Stone Representation Theorem. Halpin, J. F. (1991). ‘What is the logical form of probability assignment in quantum mechanics?’  Philosophy of Science  58 : 36–60. Looks at a number of proposals taking into account the work of Stalnaker and Lewis on counterfactuals. Hardegree, G. M. (1975). ‘Stalnaker conditionals and quantum logic.’  Journal of Philosophical Logic  4 : 399–421. The papers by Hardegree are useful reading as background to Chapter 5.

 — (1976). ‘The conditional in quantum logic.’ In  Logic and Probability in Quantum Mechanics , P. Suppes(ed.),D.Reid el Publishing Company, pp. 55–72. The material in this paper is drawn on signiﬁcantly for Chapter 5 on conditonal logic for IR.

 — (1979). ‘The conditional in abstract and concrete quantum logic.’ In  Logico-Algebraic Approach to Quantum Mechanics.  II. C. A. Hooker (ed.), D. Reidel Publishing Company, pp. 49–108. This is a much more extensive paper than Hardegree (1976). It deals with a taxonomy of quantum logics. The emphasis is still on the conditional.

 — (1982). ‘An approach to the logic of natural kinds.’  Paciﬁc Philosophical Quarterly 63 : 122–132. This paper is relevant to Chapter 2, and would make good background reading. Harman, D. (1992). Ranking algorithms. In  Information Retrieval – Data Structures, and Algorithms , Frakes, W. B. and R. Baeza-Yates (eds.), Prentice Hall, pp. 363–392. Harper, W. L., R. Stalnaker and G. Peare eds. (1981).  Ifs . Reidel. This contains reprints of a number of inﬂuential papers on counterfactual reasoning and conditionals. In particular it contains important classic papers by Stalnaker and Lewis. Hartle, J. B. (1968). ‘Quantum mechanics of individual systems.’  American Journal of Physics  36 (8): 704–712. A paper on an old debate: does it make sense to make probabilistic assertions about individual systems, or should we stick to only making assertions about ensembles?  

Healey, R. (1990).  The Philosophy of Quantum Mechanics. An Interactive Interpretation , Cambridge University Press. Despite its title this is quite a technical book. The idea of interaction is put centre stage and is to be compared with the approach by Kochen and Specker (1965a). Hearst, M. A. and J. O. Pedersen (1996). ‘Re-examining the cluster hypothesis: scatter/gather on retrieval results.’  Proceedings of the 19th Annual ACM SIGIR Conference.  pp. 76–84. Another test of the cluster hypothesis. Heelan, P. (1970a). ‘Quantum and classical logic: their respective roles.’  Synthese  21 : 2–23. An attempt to clear up some of the confused thinking about quantum logics. Heelan, P. (1970b). ‘Complementarity, context dependence, and quantum logic.’  Foun- dations of Physics  1 (2): 95–110. Mainly interesting because of the role that context plays in descriptions of quantum-mechanical events. Heisenberg, W. (1949).  The Physical Principles of the Quantum Theory , Dover Publications, Inc. By one of the pioneers of QM. It is mainly of historical interest now. Hellman, G. (1981). ‘Quantum logic and the projection postulate.’  Philosophy of Science 48 : 469–486. Another forensic examination of the ‘Projection Postulate’. Herbut, F. (1969). ‘Derivation of the change of state in measurement from the concept of minimal measurement.’  Annals of Physics  55 : 271–300. A detailed account of how to deﬁne a simple and basic concept of physical measurement for an arbitrary observable. Draws on the research surrounding the L¨ uders–Von Neumann debate on the projection postulate. The paper is well written and uses sensible notation. — (1994). ‘On state-dependent implication in quantum mechanics.’  J. Phys. A: Math. Gen.  27 : 7503–7518. This paper should be read after Chapter 5 in GIR. Hiley, B. J. and F. D. Peat (1987).  Quantum Implications. Essays in honour of David Bohm . Routlege & Kegan Paul. The work of David Bohm, although much respected, was controversial. He continued to work on hidden variable theories despite the so-called impossibility proofs. The contributors to this volume include famous quantum physicists, such as Bell and Feynman, and well known popularisers, such as Kilmister and Penrose. A book worth dipping into. It contains the article by Feynman on negative probability. Hirvensalo, M. (2001).  Quantum Computing , Springer-Verlag. A clearly written book with good appendices to quantum physics and its mathematical background. Holland, S. P. (1970). ‘The current interest in orthomodular lattices.’  Trends in Lattice Theory , J. C. Abbott (ed.). Van Nostrand Reinhold. There are many introductions to lattice theory. What distinguishes this one is that it relates the material to subspace structures of Hilbert space and to quantum logic. The explanations are relatively complete and easy to follow. Hooker, C. A., ed. (1975).  The Logico-Algebraic Approach to Quantum Mechanics . Vol. 1:  Historical Evolution . The University of Western Ontario Series in Philoso- phy of Science. D. Reidel Publishing Company. This is Volume 1 of a two-volume set containing a number of classic papers, for example, reprints of Birkhoff and Von Neumann (1936), Gleason (1957), Kochen and Specker (1965b) and Holland (1970). Hooker, C. A., ed. (1979).  The Logico-Algebraic Approach to Quantum Mechanics. Vol. 2:  Contemporary Consolidation . The University of Western Ontario Series in Philosophy of Science. D. Reidel Publishing Company. Following the historical  

papers in Volume 1, this second volume contains more recent material. A useful paper is Hardegree (1979) as a companion to Hardegree (1976). Horn, R. A. and C. R. Johnson (1999).  Matrix Analysis , Cambridge University Press. One of several well-known, standard references on matrix theory, excellent companion for Golub and Van Loan (1996). Hughes, R. I. G. (1982). ‘The logic of experimental questions.’  Philosophy of Science 1 : 243–256. A simple introduction to how a quantum logic arises out of giving a mathematical structure to the process of asking experimental questions of a quantum system. Chapter 5 of Jauch (1968) gives a more detailed account of this mode of description, and presents the necessary preliminary mathematics in the earlier chapters. This particular way of viewing the logic of quantum mechanics was also explained synoptically by Mackey (1963). — (1989).  The Structure and Interpretation of Quantum Mechanics . Harvard University Press. A lucid and well-written book. It introduces the relevant mathematics at the point where it is needed. It contains an excellent discussion of Gleason’s Theorem. It has a good chapter on quantum logic. It also introduces density operators in a simple manner. Much attention is paid to the philosophical problem of ‘properties’. An appendix contains an annotated version of the proof of Gleason’s Theorem by Cooke  et al.  (1985). Huibers, T. (1996).  An Axiomatic Theory for Information Retrieval . Katholieke Univer- sity Nijmegen. Presents a formal set of inference rules that are intended to capture retrieval. A proof system is speciﬁed for the rules, and used to prove theorems about ‘aboutness’. Ingwersen, P. (1992).  Information Retrieval Interaction . Taylor Graham. This is a for- mulation of IR from a cognitive standpoint. In many ways it is in sympathy with the approach taken in GIR, especially in that it puts interaction with the user at the centre of the discipline. Its approach is non-mathematical. Isham, C. J. (1989).  Lectures on Groups and Vector Spaces for Physicists . World Scientiﬁc. A well-paced introduction to vector spaces amongst other things. It starts from ﬁrst principles and introduces groups before it discusses vector spaces. Gives examples from physics and quantum mechanics. It is a good companion volume to Isham (1995). Isham, C. J. (1995).  Lectures on Quantum Theory: Mathematical and Structural Foun- dations . Imperial College Press. The two books by Isham (1989,1995) go together. This book is a fairly complete lecture course on QM. The 1989 book contains a thorough introduction to vector spaces which is needed for the book on QM. Although a technical introduction, it also contains considerable philosophical com- ment and is very readable. In introducing quantum theory it begins with a statement of four simple rules that deﬁne a general mathematical framework within which all quantum-mechanical systems can be described. Technical developments come after a discussion of the rules. Jauch, J. M. (1968).  Foundations of Quantum Mechanics , Addison-Wesley Publishing Company. Another classic monograph on QM. Jauch is a proponent of the mode of description of physical systems in terms of so-called ‘yes-no experiments’. Section 3-4 on projections is extremely interesting, it shows how the operation of union and intersection of subspaces are expressed algebraically in terms of the corresponding projections. An excellent introduction, one of the best, to the foundations of QM.  

— (1972). ‘On bras and kets.’ In  Aspects of Quantum Theory , A. Salam and E. P. Wigner (eds.). Cambridge University Press, pp. 137–167. Exactly that!

 — (1973).  Are Quanta Real? A Galilean Dialogue . Indiana University Press. A three- way discussion written by a ﬁne quantum physicist. Perhaps this could be read after the prologue in GIR which has been done in the same spirit. It contains a physical illustration, in terms of polarising ﬁlters, of the intrinsic probability associated with measuring a property of a single photon.

 — (1976). ‘The quantum probability calculus.’ In  Logic and Probability in Quantum Mechanics ,  Suppes,  $P_{\cdot}$   (ed.). D. Reidel Publishing Company, pp. 123–146. Starting with the classical probability calculus, it gives an account, from ﬁrst principles, of the probability calculus in quantum mechanics. Jaynes, E. T. (2003).  Probability Theory: The Logic of Science . Cambridge University Press. Jaynes’  magnum opus . He is has worked for many years on probability theory and maximum entropy. This book is the result of over sixty years of thinking about the nature of probability: it is a  tour de force . It is one of the best modern reference works on probability. It contains a good annotated bibliography. Jeffrey, R. C. (1983).  The Logic of Decision . University of Chicago Press. This is the best source for a discussion of Jeffrey Conditional is ation and the role that the ‘passage of experience’ plays in that. The Von Neumann projection postulate can be related to this form of cond i tonal is ation (see Van Fraassen, 1991, p. 175). Jeffreys, H. (1961).  Theory of Probability . Oxford University Press. One of the classic introductions to probability theory. Jeffreys is sometimes associated with the sub- jectivist school of probability – which is somewhat surprising since he was he was a distinguished mathematical physicist. He was an early proponent of Bayesian inference and the use of priors. The ﬁrst chapter on fundamental notions is still one of the best elementary introductions to probable inference ever written. Jordan, T. F. (1969).  Linear Operators for Quantum Mechanics , John Wiley & Sons, Inc. There are a number of books frequently referred to in the quantum mechanics literature for the relevant background mathematics. Here we have identiﬁed three: Jordan (1969), Fano (1971) and Reed and Simon (1980). All three cover similar material, perhaps Reed and Simon is the most pure-mathematical in approach, whereas Jordan makes explicit connections with quantum mechanics. K¨ agi-Romano, U. (1977). ‘Quantum logic and generalized probability theory.’  Jour- nal of Philosophical Logic  6 : 455–462. A brief attempt to modify the classical Kolmogorov (1933) theory so that it becomes applicable to quantum mechanics. Keynes, M. (1929).  A Treatise on Probability . Macmillan. Keynes’ approach to prob- ability theory represents a logical approach; probability is seen as a logical rela- tion between propositions. After Frank Ramsey’s devastating critique of it, it lost favour. However, it may be that there is more to be said about Keynes’ theory, espe- cially in the light of the way quantum probability is deﬁned. The ﬁrst one hundred pages of Keynes’ treatise is still a wonderful historical account of the evolution of the theory of probability – full of insights that challenge the foundations of the subject. Kochen, S. and E. P. Specker (1965a). ‘Logical structures arising in quantum theory.’ In Symposium on the Theory of Models , eds. J. Addison, J. L. Henkin and A. Tarski. North Holland, pp. 177–189. An early account of how logical structures arise in quantum theory by two eminent theoreticians.  

— (1965b). ‘The calculus of partial propositional functions.’ In  Logic, Methodology, and Philosophy of Science . Y. Bar-Hillel (ed.). North-Holland, pp. 45–57. A follow-on paper to their earlier 1965 paper; in fact here they deny a conjecture made in the ﬁrst paper. Kolmogorov, A. N. (1950).  Foundations of the theory of probability . Chelsea Pub- lishing Co. Translation of Kolmogorov’s original 1933 monograph. An approach to probability theory phrased in the language of set theory and measure theory. Kolmogorov’s axiomatisation is now the basis of most current work on probability theory. For important dissenters consult Jaynes (2003). Korfhage, R. R. (1997).  Information Storage and Retrieval . Wiley Computer Publish- ing. A simple and elementary introduction to information retrieval, presented in a traditional way. Kowalski, G. J. and M. T. Maybury (2000).  Information Retrieval Systems: Theory and Implementation . Kluwer. ‘This work provides a theoretical and practical explana- tion of the advancements in information retrieval and their application to exist- ing systems. It takes a system approach, discussing all aspects of an Information Retrieval System. The major difference between this book and the ﬁrst edition is the addition to this text of descriptions of the automated indexing of multimedia documents, as items in information retrieval are now considered to be a combina- tion of text along with graphics, audio, image and video data types.’ – publisher’s note. Kyburg, H. E., Jr. and C. M. Teng (2001).  Uncertain Inference . Cambridge University Press. A comprehensive, up-to-date survey and explanation of various theories of uncertainty. Has a good discussion on the range of interpretations of probability. Also, does justice to Dempster–Shafer belief revision. Covers the work of Carnap and Popper in some detail. Lafferty, J. and C. X. Zhia (2003). ‘Probabilistic relevance models based on document and query generation.’ In  Language Modeling for Information Retrieval . W. B. Croft and J. Lafferty (eds.). Kluwer, pp. 1–10. A very clear introduction to language modeling in IR. Lakoff, G. (1987).  Women, Fire, and Dangerous Things. What Categories Reveal about the Mind . The University of Chicago Press. A wonderfully provocative book about the nature of classiﬁcation. It also discusses the concept of natural kinds in a number of places. A real page turner. Lavrenko, V. and W. B. Croft (2003). ‘Relevance models in information retrieval.’ In Language Modeling for Information Retrieval . W. B. Croft and J. Lafferty (eds.). Kluwer. Describes how relevance can be brought into language models. Also, draws parallels between language models and other forms of plausible inference in IR. Lewis, D. (1973).  Counterfactuals . Basil Blackwell. Classic reference on the possible world semantics for counterfactuals. — (1976). ‘Probabilities of conditionals and conditional probabilities.’  Philosophy of Science  85 : 297–315. Lewis shows here how the Stalnaker Hypothesis is subject to a number of triviality results. He also deﬁnes a process known as  imaging  that was used in Crestani and Van Rijsbergen (1995a) to evaluate the probability of conditonals in IR.  

Lo, H.-K., S. Popescu and T. Spiller, eds. (1998).  Introduction to Quantum Computation and Information . World Scientiﬁc Publishing. A collection of semi-popular papers on quantum computation. Mathematics is kept to a minimum. Lock, P. F. and G. M. Hardegree (1984). ‘Connections among quantum logics. Part 1. Quantum propositional logics.’  International Journal of Theoretical Physics  24 (1): 43–61. The work of Hardegree is extensively used in Chapter 5 of GIR. Lockwood, M. (1991).  Mind, Brain and the Quantum. The Compound ‘I’ . Blackwell Publishers. This book is concerned with QM and consciousness. It is almost entirely philosophical and uses almost no mathematics. It should probably be read at the same time as Penrose (1989, 1994). Lomonaco, S. J., Jr., ed. (2002).  Quantum Computation: A Grand Mathematical Chal- lenge for the Twenty-First Century and the Millennium . Proceedings of Symposia in Applied Mathematics. Providence, Rhode Island, American Mathematical Society. The ﬁrst lecture by Lomonaco, ‘A Rosetta stone for quantum mechanics with an introduction to quantum computation’, is one of the best introductions this author has seen. It accomplishes in a mere 65 pages what most authors would need an entire book for. The material is presented with tremendous authority. A good collection of references. London, F. and E. Bauer (1982). ‘The theory of observation in quantum mechanics.’ In  Quantum Theory and Measurement . J. A. Wheeler and W. H. Zurek (eds.) Princeton University Press, pp. 217–259. The authors claim this to be a ‘treatment both concise and simple’ as an introduction to the problem of measurement in quantum mechanics. They have taken their cue from Von Neumann’s original 1932 foundations and tried to make his deep discussions more accessible. They have succeeded. The original version was ﬁrst published in 1939 in French. L¨ uders, G. (1951). ‘  Uber die Zustands¨ anderung durch den Messprozess.’  Annalen der Physik  8 : 323–328. The original paper by L¨ uders that sparked the debate about the Projection Postulate. Mackay, D. (1950). ‘Quantal aspects of scientiﬁc information’,  Philosophical Magazine , 41 , 289–311. — (1969).  Information, Mechanism and Meaning , MIT Press. Mackey, G. W. (1963).  Mathematical Foundations of Quantum Mechanics . Benjamin. One of the early well known mathematical introductions, it is much cited. He introduced the suggestive terminology ‘question-valued measure’. Marciszewski, W., ed. (1981).  Dictionary of Logic – as Applied in the Study of Language . Nijhoff International Philosophy Series, Martinus Nijhoff Publishers. This dictio- nary contains everything that you have always wanted to know about logic (but were ashamed to ask). It contains entries for the most trivial up to the most sophisticated. Everything is well explained and references are given for further reading. Maron, M. E. (1965). ‘Mechanized documentation: The logic behind a probabilistic interpretation.’ In  Statistical Association Methods for Mechanized Documenta- tion . M. E. Stevens  et al ., (eds.) National Bureau of Standards Report  269 : 9–13. ‘The purpose of this paper is to look at the problem of document identiﬁcation and retrieval from a logical point of view and to show why the problem must be inter- preted by means of probability concepts.’ This quote from Maron could easily be taken as a part summary of the approach adopted in GIR. Maron was one of the very  

ﬁrst to start thinking along these lines, less surprising if one considers that Maron’s Ph.D. dissertation, ‘The meaning of the probability concept’, was supervised by  

Hans Reichenbach, one of early contributors to the foundations of QM. Martinez, S. (1991). ‘L¨ uders’s rule as a description of individual state transformations.’ Philosophy of Science  58 : 359–376. L¨ uders paper on the projection postulate gener- alising Von Neumann’s rule has played a critical role in quantum theory. A number of papers have examined it in detail. Here is one such paper. Mirsky, L. (1990).  An Introduction to Linear Algebra . Dover Publications, Inc. A tra- ditional introduction emphasising matrix representation for linear operators. It contains a nice chapter on orthogonal and unitary matrices, an important class of matrices in QM. This material is used in Chapter 6 to explain relevance feedback. Mittelstaedt, P. (1972). ‘On the interpretation of the lattice of subspaces of the Hilbert space as a propositional calculus.’  Zeitschrift f¨ ur Naturforschung  27a : 1358–1362. Here is a very nice and concise set of lattice-theoretic results derived from the original paper by Birkhoff and Von Neumann (1936). In particular it shows how a quasi-implication, deﬁned in the paper, is a generalisation of classical implication. — (1998).  The Interpretation of Quantum Mechanics and the Measurement Process . Cambridge University Press. A recent examination of the measurement problem in QM. Mizzaro, S. (1997). ‘Relevance: the whole history.’  Journal of the American Society for Information Science  48 : 810–832. Mizzaro brings the debate on ‘relevance’ up to date. It is worth reading Saracevic (1975) ﬁrst. Murdoch, D. (1987).  Niels Bohr’s Philosophy of Physics  Cambridge University Press. This is of historical interest. Amongst other things it traces the development of Bohr’s ideas on complementarity. Worth reading at the same time as Pais’ (1991) biography of Bohr. Nie, J.-Y., M. Brisebois and F. Lepage (1995). ‘Information retrieval as counterfactual.’ The Computer Journal  38 (8): 643–657. Looks at IR as counterfactual reasoning, drawing heavily on Lewis (1973). Nie, J.-Y. and F. Lepage (1998). ‘Toward a broader logical model for information retrieval.’ In  Information Retrieval: Uncertainty and Logics: Advanced Models for the Representation and Retrieval of Information.  F. Crestani, M. Lalmas and C. J. van Rijsbergen (eds.). Kluwer: 17–38. In this paper the logical approach to IR is revisited and the authors propose that situational factors be included to enlarge the scope of logical modelling. Nielsen, M. A. and I. L. Chuang (2000).  Quantum Computation and Quantum Informa- tion  Cambridge University Press. Without doubt this is currently one of the best of its kind. The ﬁrst one hundred pages serves extremely well as an introduction to quantum mechanics and its relevant mathematics. It has a good bibliography with references to www.arXiv.org whenever a paper is available for downloading. It is also well indexed. Ochs, W. (1981). ‘Some comments on the concept of state in quantum mechanics.’ Erkenntnis  16 : 339–356. The notion of state is fundamental both in classical and quantum mechanics. The difference between a pure and mixed state in QM is of some importance, and the mathematics is designed to reﬂect this difference. There  

is an interpretation of mixed states as the ‘ignorance interpretation of states’. Here is a discussion of that interpretation. Omn\` es, R. (1992). ‘Consistent interpretations of quantum mechanics.’  Reviews of Mod- ern Physics  64 (2): 339–382. Excellent supplementary reading to Grifﬁths (2002).

 — R. (1994).  The Interpretation of Quantum Mechanics  Princeton University Press. A complete treatment of the interpretation of QM. It is hard going but all the necessary machinery is introduced. There is a good chapter on a logical framework for QM. Gleason’s Theorem is presented. His other book, Omn\` es (1999), is a much more leisurely treatment of some of the same material.

 — (1999).  Understanding Quantum Mechanics  Princeton University Press. See Omnes (1994). Packel, E. W. (1974). ‘Hilbert space operators and quantum mechanics.’  American Mathematical Monthly  81 : 863–873. Convenient self-contained discussion of Hilbert space operators and QM. Written with mathematical rigour. Pais, A. (1991).  Niels Bohr’s Times, in Physics, Philosophy, and Polity , Oxford Univer- sity Press. A wonderful book on the life and times of Niels Bohr. Requisite reading before seeing the play  Copenhagen  by Michael Frayn. Park, J. L. (1967). ‘Nature of quantum states.’ American Journal of Physics  36 : 211– 226. Yet another paper on states in QM. This one explains in detail the difference between pure and mixed states. Parthasarathy, K. R. (1970). ‘Probability theory on the closed subspaces of a Hilbert space.’  Les Probabilites sur Structures Algebriques , CNRS.  186 : 265–292. An early version of a proof of Gleason’s Theorem, it is relatively self-contained. The version in the author’s 1992 book may be easier to follow since the advanced mathematics is ﬁrst introduced. — (1992).  An Introduction to Quantum Stochastic Calculus , Birkh¨ auser Verlag. The ﬁrst chapter on events, observable and states is an extraordinarily clear and condensed exposition of the underlying mathematics for handling probability in Hilbert space. Central to the chapter is yet another proof of Gleason’s Theorem. The mathematical concepts outer product and trace are very clearly deﬁned. Pavicic, M. (1992). ‘Bibliography on quantum logics and related structures.’  Inter- national Journal of Theoretical Physics  31 (3): 373–461. A useful bibliography emphasising papers on quantum logic. Penrose, R. (1989).  The Emperor’s New Mind: Concerning Computers, Minds, and the Laws of Physics , Oxford University Press. A popular book containing a section on quantum magic and mystery, writtten with considerable zest. — (1994).  Shadows of the Mind. A Search for the Missing Science of Consciousness , Oxford University Press. A popular book containing a substantial section on the quantum world. Peres, A. (1998).  Quantum Theory: Concepts and Methods , Kluwer Academic Publish- ers. This book is much liked by researchers in quantum computation for providing the necessary background in quantum mechanics. Contains good discussion of Bell’s inequalities, Gleason’s Theorem and the Kochen–Specker Theorem. Petz, D. and J. Zem´ anek (1988). Characterizations of the Trace.  Linear Algebra and Its Applications , Elsevier Science Publishing.  111 : 43–52. Useful if you want to know more about the properties of the trace function.  

Pippard, A. B., N. Kemmer, M. B. Hesse, M. Pryce, D. Bohn and N. R. Hanson (1962). Quanta and Reality , The Anchor Press Ltd. Popular book. Piron, C. (1977). ‘On the logic of quantum logic.’  Journal of Philosophical Logic  6 : 481–484. A clariﬁcation of the connection between classical logic and quantum logic. Very short and simply written. Pitowsky, I. (1989).  Quantum Probability – Quantum Logic  Springer-Verlag. A thorough and detailed analysis of the two ideas. Many of the arguments are illustrated with simple concrete examples. Recommended reading after ﬁrst consulting Appendix III in GIR. Pittenger, A. O. (2000).  An Introduction to Quantum Computing Algorithms , Birkh¨ auser. A slim volume giving a coherent account of quantum computation. Plotnitsky, A. (1994).  Complementarity. Anti-Epistemology after Bohr and Derrida , Duke University Press. Incomprehensible but fun. Polkinghorne,J.C.(1986). TheQuantumWorld .Pelican.Elementary,shortandsimple.It also contains a nice glossary; for example,  non-locality  – the property of permitting a cause at one place to produce immediate effects at a distant place. — (2002).  Quantum Theory: a Very Short Introduction . Oxford University Press. The title says it all. Nice mathematical appendix. Popper, K. R. (1982).  Quantum Theory and the Schism in Physics  Routledge. An exhila- rating read. Popper is never uncontroversial! Contains a thought-provoking analysis of the Heisenberg Uncertainty Principle. Priest, G. (2001).  An Introduction to Non-classical Logic . Cambridge University Press. An easy-going introduction to non-classical logics. It begins with classical logic, emphasising the material conditional, and then moves on to to the less standard logics. The chapter devoted to conditional logics is excellent and worth reading as background to the logical discussion in Chapter 5 in GIR. Putnam, H. (1975). ‘The logic of quantum mechanics.’ In  Mathematics, Matter and Method: Philosophical Papers , vol. I (ed.). H. Putnam. Cambridge University Press. pp. 174–197. The revised version of the 1968 paper that sparked a continuing debate about the nature of logic, arguing that ‘logic is, in a certain sense, a natural science’. — (1981). ‘Quantum mechanics and the observer.’  Erkenntnis  16 : 193–219. A revision of some of Putnam’s views as expressed in Putnam (1975). Quine, W. v. O. (1969).  Ontological Relativity and Other Essays . Columbia University Press. Contains a Chapter on natural kinds that is relevant to Chapter 2 of GIR. Rae, A. (1986).  Quantum Physics: Illusion or Reality?  Cambridge University Press. A ﬁne short popular introduction to quantum mechanics. R´ edei, M. (1998).  Quantum Logic in Algebraic Approach  Kluwer Academic Publishers. A very elaborate book on quantum logic and probability. It builds on the early work of Von Neumann. It mainly contains pure mathematical results and as such is a useful reference work. To be avoided unless one is interested in pursuing quantum logic (and probability) on various kinds of lattices in great depth. R´ edei, M. and M. St¨ oltzner, eds. (2001).  John von Neumann and the Foundations of Quantum Physics . Vienna Circle Institute Yearbook, Kluwer Academic Publish- ers. A collection of papers dealing with the contributions that John von Neumann made to QM. It also contains some previously unpublished material by John von Neumann. One of the unpublished lectures, ‘Unsolved Problems in Mathematics’, is extensively quoted from in Chapter 1.  

Redhead, M. (1999).  Incompleteness Non-locality and Realism. A Prolegomenon to the Philosophy of Quantum Mechanics , Clarendon Press. Although philosophical in thrust and intent, it is quite mathematical. It gives a competent introduction to QM. The Einstein–Podolsky–Rosen incompleteness argument is discussed, followed by non-locality and the Bell inequality as well the Kochen–Specker Paradox. It has a good mathematical appendix. Reed, M. and B. Simon (1980).  Methods of Modern Mathematical Physics , Vol. I Functional Analysis  Academic Press. Compare this book with Fano (1971) and Jordan (1969). Reichenbach, H. (1944).  Philosophic Foundations of Quantum Mechanics , University of California Press. Still a valuable and well-written account. His views on multi- valued and three-valued logic for QM are now discounted. Retherford, J. R. (1993).  Hilbert Space: Compact Operators and the Trace Theorem , Cambridge University Press. Slim volume, worth consulting on elementary spectral theory. Richman, F. and D. Bridges (1999). ‘A constructive proof of Gleason’s Theorem.’  Jour- nal of Functional Analysis  162 : 287–312. Another version of the proof of Gleason’s Theorem. Riesz, F. and B. Sz.-Nagy (1990).  Functional Analysis , Dover Publications, Inc. A classic reference on functional analysis. It contains a good section on self-adjoint transformations. Robertson, S. E. (1977). ‘The probability ranking principle in IR.’  Journal of Docu- mentation  33 : 294–304. A seminal paper. It is the ﬁrst detailed formulation of why ranking documents by the probability of relevance can be optimal. Contains an interesting discussion of the principle in relation to the Cluster Hypothesis, and makes reference to Goffman’s early work. It is reprinted in Sparck Jones and Willett (1997). Rom´ an, L. (1994). ‘Quantum logic and linear logic.’  International Journal of Theoretical Physics  33 (6): 1163–1172. Linear logic is an important development in computer science; here is a paper that clariﬁes its relation to quantum logic. Roman, S. (1992).  Advanced Linear Algebra , Springer-Verlag. A fairly recent textbook on linear algebra. Excellent chapter on eigenvectors and eigenvalues. Sadun, L. (2001).  Applied Linear Algebra. The Decoupling Principle  Prentice Hall. It is hard to ﬁnd any textbooks on linear algebra that deal with bras, kets and duality. This is such a rare ﬁnd. It also discusses the Heisenberg Uncertainty Principle for bandwidth and Fourier transforms, that is, independent of QM. Apart from that, it is a clear and well presented introduction to linear algebra. Salton, G. (1968).  Automatic Information Organization and Retrieval  McGraw-Hill Book Company. A classic IR reference. This is a compendium of early results in IR based on the Smart system that was originally designed at Harvard between 1962 and 1965. It continues to operate at Cornell to this day. Even though this book is dated it still contains important ideas that are not readily accessible elsewhere. Salton, G. and M. J. McGill (1983).  Introduction to Modern Information Retrieval , McGraw-Hill Book Company. An early textbook on IR, still much used and cited. Saracevic, T. (1975). ‘Relevance: A review of and a framework for the thinking on the notion in information science.’  Journal of the American Society for Informa- tion Science  26 : 321–343. Although somewhat dated, this is still one of the best  

conceptualising relevance. One gets a more up-to-date view of this topic by reading Mizzaro (1997), and the appropriate sections in Belew (2000). Schmeidler, W. (1965).  Linear Operators in Hilbert Space  Academic Press. A gentle introduction to linear operators in Hilbert space, it begins with a simple introduction to Hilbert spaces. Schr¨ odinger, E. (1935). ‘Die gegenwartige Situation in der Quantenmechanik.’  Natur- wissenschaften  22 : 807–812, 823–828, 844–849. The original of the translated version in Wheeler and Zurek (1983, pp. 152–167). In our Prologue there is a quote from the translation. Schr¨ odinger was at odds with the quantum mechan- ics orthodoxy for most of his life. He invented the Schr¨ odinger’s Cat Paradox to illustrate the absurdity of some of its tenets. Schwarz, H. R., H. Rutishauser and E. Stiefel (1973).  Numerical Analysis of Symmetric Matrices . Prentice-Hall, Inc. Despite its title this is an excellent introduction to vector spaces and linear algebra. The numerical examples are quite effective in aiding the understanding of the basic theory. It uses a very clear notation. Schwinger, J. (1959). ‘The algebra of microscopic measurement.’  Proceedings of the National Academy of Science  45 : 1542–1553. Full version of the paper reprinted in Schwinger (1991).

 — (1960). ‘Unitary operator bases.’  Proceedings of the National Academy of Science 46 : 570–579. Reprinted in Schwinger (1991).

 — (1960). ‘The geometry of quantum states.’  Proceedings of the National Academy of Science  46 : 257–265. Reprinted in Schwinger (1991).

 — (1991).  Quantum Kinematics and Dynamics , Perseus Publishing. A preliminary and less formal version of material in Schwinger (2001). This is a good book to start with if one wishes to read Schwinger in detail.

 — (2001).  Quantum Mechanics: Symbolism of Atomic Measurements , Springer-Verlag. Schwinger received the Nobel prize for physics at the same time as Feynman in 1965. His approach to QM was very intuitive, motivated by the process of measurement. The ﬁrst chapter introduces QM through the notion of measurement algebra. It is an idiosyncratic approach but some may ﬁnd it a more accessible way than through Hilbert space theory. Sibson, R. (1972). ‘Order invariant methods for data analysis.’  The Journal of the Royal Statistical Society, Series B(Methodology)  34 (3): 311–349. A lucid discussion on classiﬁcation methods without recourse to details of specifc algorithms. Simmons, G. F. (1963).  Introduction to Topology and Modern Analysis , McGraw-Hill. Contains an excellent introduction to Hilbert spaces. Sneath, P. H. A. and R. R. Sokal (1973).  Numerical Taxonomy , W. H. Freeman and Company. An excellent compendium on classiﬁcation methods. Although now over thirty years old, it is still one of the best books on automatic classiﬁcation. It contains an very thorough and extensive bibliography. Sneed, J. D. (1970). ‘Quantum mechanics and classical probability theory.’  Synthese  21 : 34–64. The author argues that ‘there is an interpretation of the quantum mechan- ical formalism which is both physically acceptable and consistent with classical probability theory (Kolmogorov’s)’. Sober, E. (1985). ‘Constructive empiricism and the problem of aboutness.’  British Jour- nal of the Philosophy of Science  1985: 11–18. The concept of ‘aboutness’ is a source of potential difﬁculty in IR. Here is a philosophical discussion of the notion.  

Sparck Jones, K. and P. Willett, eds. (1997).  Readings in Information Retrieval . The Morgan Kaufmann Series in Multimedia Information and Systems, Morgan Kauf- mann Publishers, Inc. A major source book for important IR papers published in the last ﬁfty years. It contains, for example, the famous paper by Maron and Kuhns. It also has a chapter on models describing the most important ones. Not covered are latent semantic indexing and language models in IR. Stairs, A. (1982). ‘Discussion: quantum logic and the L¨ uders rule.’  Philosophy of Science 49 : 422–436. Contribution to the debate sparked by Putnam (1975). A response to the Friedman and Putnam (1978) paper. Stalnaker, R. (1970). ‘Probability and conditionals.’  Philosophy of Science  37 : 64–80. It is here that Stalnaker stated the Stalnaker Hypothesis that the probability of a conditional goes as the conditional probability. David Lewis subsequently produce a set of triviality results. All this is well documented in Harper  et al . (1981). Suppes, P., ed. (1976).  Logic and Probability in Quantum Mechanics . Synthese Library. D. Reidel Publishing Company. This still remains one of the best collections of papers on logic and probability in quantum mechanics despite its age. It con- tains an excellent classiﬁed bibliography of almost one thousand references. The headings of the classiﬁcation are very helpful, for example, ‘quantum logic’ is a heading under which one will ﬁnd numerous references to items published before 1976. It is well indexed: the author index gives separate access to the bibliography. Sutherland, R. I. (2000). ‘A suggestive way of deriving the quantum probability rule.’ Foundations of Physics Letters  13 (4): 379–386. An elementary and simple deriva- tion of the rule that probability in QM goes as the ‘modulus squared’. Teller, P. (1983). ‘The projection postulate as a fortuitous approximation.’  Philosophy of Science  50 : 413–431. Another contribution to the debate sparked by Friedman and Putnam (1978). It also contains an excellent section on the Projection Postulate. Thomason, R. H., ed. (1974).  Formal Philosophy: Selected papers of Richard Montague . Yale University Press. Once one has read the introduction by Dowty  et al . (1981) on Montague Semantics one may wish to consult the master. Thomason has collected together probably the most important papers published by Montague. Montague’s papers are never easy going but always rewarding. Tombros, A. (2002).  The Effectiveness of Query-based Hierarchic Clustering of Documents for Information Retrieval. Computing Science Department , Glasgow University. A thorough examination of document clustering. Contains a very good up-to-date literature survey. There is an excellent discussion on how to measure the effectiveness of document clustering. Van der Waerden, B. L., ed. (1968).  Sources of Quantum Mechanics , Dover Publications, Inc. Contains original papers by Bohr, Born, Dirac, Einstein, Ehrenfest, Jordan, Heisenberg and Pauli, but sadly omits any by Schr¨ odinger. Van Fraassen, B. C. (1976). ‘Probabilities of conditionals.’ In  Foundations of Probability Theory, Statistical Inference, and Statistical Theories of Science . W. L. Harper and C. A. Hooker (eds.). Reidel, pp. 261–300. This is a beautifully written paper, it examines the Stalnaker Thesis afresh and examines under what conditions it can be sustained. — (1991).  Quantum Mechanics. An Empiricist View  Clarendon Press. This is a superb introduction to modern quantum mechanics. Its notation is slightly awkward, and it avoids the use of Dirac notation. It aims to present and discuss a number of interpretations of quantum mechanics. For example, there is an extensive con- sideration of modal interpretations. Hilbert space theory is kept to a minimum. The mathematics is intended to be understood by philosophers with little or no  

background. Van Rijsbergen, C. J. (1970). ‘Algorithm 47. A clustering algorithm.’  The Computer Journal  13 : 113–115. Contains a programme for the  $\mathrm{~L~}^{*}$    algorithm mentioned in Chapter 2.

 — (1979a).  Information Retrieval . Butterworths. A popular textbook on IR, still much used. It has been made available on number of web sites, for example, a search with Google on the author’s name will list www.dcs.gla.ac.uk/Keith/Preface.html. An electronic version on CD is also contained in Belew (2000).

 — (1979b). ‘Retrieval effectiveness.’ In  Progress in Communication Sciences . M. J. Voigt and G. J. Hanneman, (eds.). ABLEX Publishing Corporation. Vol. I, pp. 91– 118. A foundational paper on the measurement of retrieval effectiveness, paying particular attention to averaging techniques. Expresses some of the standard param- eters of effectiveness, such as precision and recall, in terms of general measures.

 — (1979c). ‘Foundation of evaluation.’  Journal of Documentation  30 : 365–373. Con- tains a complete derivation of the E and F measure for measuring retrieval effec- tiveness based on the theory of measurement.

 — (1986). ‘A non-classical logic for information retrieval.’  The Computer Journal  29 : 481–485. The paper that launched a number of papers dealing with the logical model for information retrieval. Reprinted in Sparck Jones and Willett (1997).

 — (1992) ‘Probabilistic retrieval revisited.’  The Computer Journal  35 : 291–298.

 — (1996).  Information, Logic, and Uncertainty in Information Science . CoLIS 2, Second International Conference on Conceptions of Library and Information Science: Inte- gration in Perspective, Copenhagen, The Royal School of Librarianship. Here is the ﬁrst detailed published account of the conceptual is ation underlying the approach in GIR. An argument is made for an interaction logic taking its inspiration from quantum logic.

 — (2000). ‘Another look at the logical uncertainty principle.’  Information Retrieval  2 : 15–24. Useful background reading for Chapter 2. Varadarajan, V. S. (1985).  Geometry of Quantum Theory  Springer-Verlag. A one volume edition of an earlier, 1968, two-volume set. It contains a very detailed and thorough treatment of logics for quantum mechanics followed by logics associated with Hilbert spaces. The material is beautifully presented, a real labour of love. — (1993). ‘Quantum theory and geometry: sixty years after Von Neumann.’  Inter- national Journal of Theoretical Physics  32 (10): 1815–1834. Mainly of historical interest, but written by one of the foremost scholars of quantum theory. It reviews some of the developments in mathematical foundations of QM since the publication of Von Neumann (1932). Written with considerable informality. Von Neumann, J. (1932).  Mathematische Grundlagen der Quantenmechanik . Springer. The original edition of his now famous book on QM.

 — (1961).  Collected Works.  Vol. I:  Logic, Theory of Sets and Quantum Mechanics , Pergamon Press. This volume contains most of John von Neumann’s published papers on quantum mechanics (in German).

 — (1983).  Mathematical Foundations of Quantum Mechanics , Princeton University Press. This is the 1955 translation by Robert T. Beyer of John von Neumann (1932), originally published by Princeton University Press. It is the starting point for most work in the last 70 years on the philosophy and interpretation of quantum mechanics. It contains a so-called proof of the ‘no hidden variables’ result, a result that was famously challenged in detail by Bell (1993), and much earlier by Reichenbach (1944, p.14). Nevertheless, this book was and remains one of the great contributions to the foundations of QM. Its explanations, once the notation has been mastered,  

Von Weizs¨ acker, C. F. (1973). ‘Probability and quantum mechanics.’  British Journal of Philosophical Science  24 : 321–337. An extremely informal but perceptive account of probability in QM. Voorhees, E. M. (1985).  The Effectiveness and Efﬁciency of Agglomerative Hierar- chic Clustering in Document Retrieval. Computing Science Department , Cornell University. One of the ﬁrst thorough evaluations of the Cluster Hypothesis. Wheeler, J. A. (1980). ‘Pregeometry: motivation and prospects.’ In  Quantum Theory and Gravitation . A. R. Marlow (ed.). Academic Press, pp. 1–11. Provocative article about the importance and role of geometry in quantum mechanics. The quote: ‘No elementary phenomenon is a phenomenon until it is an observed (registered) phenomenon’ is taken from this essay. Wheeler, J. A. and W. H. Zurek, eds. (1983).  Quantum Theory and Measurement . Prince- ton University Press. Here is a collection of papers that represents a good snapshot of the state of debate about the ‘measurement problem’. Many of the classic papers on the problem are reprinted here, for example, Schr¨ odinger (1935), London and Bauer (1982) and Einstein, Podolsky and Rosen (1935). Whitaker, A. (1996).  Einstein, Bohr and the Quantum Dilemma , Cambridge University Press. Should the reader get interested in the debate between Bohr and Einstein that took place between 1920 and 1930, this is a good place to start. Wick,D.(1995). The In famous Boundary:Seven Decades of Heresy in Quantum Physics . Copernicus. This is a wonderfully lucid book about the well-known paradoxes in quantum mechanics. It is written in an informal style and pays particular attention to the history of the subject. It contains a substantial appendix on probability in quantum mechanics prepared by William G. Farris. Wilkinson, J. H. (1965).  The Algebraic Eigenvalue Problem . Clarendon Press. This is perhaps the ‘Bible’ of mathematics for dealing with the numerical solutions of the eigenvalue problem. It is written with great care. Williams, D. (2001).  Weighing the Odds: a Course in Probability and Statistics . Cam- bridge University Press. A modern introduction. It would make a good companion to Jaynes (2003) simply because it presents the subject in a neutral and mathematical way, without the philosophical bias of Jaynes. It contains a useful chapter on quan- tum probability and quantum computation: a rare thing for books on probability theory. Witten, I. H., A. Moffat and T. C. Bell (1994).  Managing Gigabytes – Compressing and Indexing Documents and Images  Van Nostrand Reinhold. A useful book about the nuts and bolts of IR. There is now a second edition published in 1999. Wootters, W. K. (1980a).  The Acquisition of Information from Quantum Measurements . Center for Theoretical Physics, Austin, The University of Texas at Austin. Wootters summarises his results in this thesis by ‘. . . the observer’s ability to distinguish one state from another seems to be reﬂected in the structure of quantum mechanics  

itself’. He gives an information-theoretic argument for a particular form of a prob- abilistic law which is used in the Prologue of this book. — (1980b). ‘Information is maximised in photon polarization measurements.’ In  Quan- tum Theory and Gravitation . A. R. Marlow (ed.). Academic Press, pp. 13–26. A self-contained account of a central idea described in the thesis by Wootters (1980a). His idea is used in the Prologue of GIR. Zeller, Eduard (1888).  Plato and the Older Academy , translated by Sarah Alleyne and Alfred Goodwin, Longmens, Green and Co., pp. 21–22, note 41. Zhang, F. (1999).  Matrix Theory: Basic Results and Techniques  Springer. A standard modern reference on matrices; contains a good chapter on Hermitian matrices.  

Abbott, J. C. Accardi, L. 24, 120 Aerts, D. 28, 114, 120, 122 Albert, David Z. 17, 27, 120 Amari, Shun-ichi 99, 120 Amati, G. 94, 120 Arveson, W. 61, 121, 130 Auletta, G. 121 Auyang, S. Y. 109, 121  

Bacciagaluppi, G. 71, 109, 121, 128 Baeza-Yates, R. 27, 87, 121, 128 Baggott, J. 114, 121 Bahadur, R. R. Barrett, Jeffrey A. 17, 27, 114, 121 Barwise, J. 40, 121 Belew, R. 26, 49, 93, 121, 140, 142 Bell, J. S. 122, 131, 143 Beltrametti, E. G. 71, 118, 122 Bigelow, J. C. 100, 122 Birkhoff, G. 11, 40, 71, 101, 118, 122, 128, 131, 136 Blair, D. C. 27, 28, 31, 123 Blum, K. 81, 123 Borland, P. 33, 92, 123 Bouwmeester, D. 115, 123 Bruza, P. D. 19, 123 Bub, J. 71, 99, 101, 109, 122, 123 Busch, P. 123 Butterﬁeld, J. 124  

Campbell, I. 14, 93, 96, 97, 124 Carnap, R. 124 Cartwright, N. 124 Cassinelli, G. 71, 118, 122 Casti, J. L. 47, 101, 124  

Cohen, D. W. 49, 98, 121, 124 Cohen-Tannoudji, C. 98 Collatz, L. 61, 124 Colodny, R. G. 124 Cooke, R. 98, 124, 129, 132 Cox, R. T. 116, 124, 125 Crestani, F. 62, 68, 70, 93, 125, 134 Croft, W. B. 93, 98, 125, 134  

d’Espagnat, B. 98, 109, 126 Dalla Chiara, M. L. 71, 125 Davey, B. A. 37, 63, 125 de Broglie, L. 125 de Finetti, B. 116, 125 Debnath, L. 101, 126 Deerwester, S. 10, 23, 126 Deutsch, David 115, 126 Deutsch, Frank 44, 126 DeWitt, B. S. 17, 120, 126 Dirac, P. A. M. 42, 61, 73, 78, 98, 107, 109, 126, 127 Diu, B. Dominich, S. 27, 93, 127 Dowty, D. 30, 127, 141 Dumais, S. T. 126  

Engesser, K. 11, 72, 127  

Fairthorne, R. A. 27, 35, 127 Fano, G. 61, 127, 133, 139 Fedullo, A. 24, 120 Feller, W. 25, 116, 127 Feynman, R. P. 109, 127 Finch, P. D. 71, 128 Fine, A. 128 Finkbeiner, D. T. 41, 50, 101, 128  

Fisher, R. A. 10, 128 Frakes, W. B. 27, 128 Friedman, A. 128 Friedman, M. 71, 123, 128, 141  

Ganter, B. 37, 128 Garden, R. W. 128 Gibbins, P. 27, 71, 99, 125, 128 Gillespie, D. T. 129 Gleason, A. M. 24, 58, 80, 119, 129, 131 Goffman, W. 33, 92, 129 Golub, G. H. 61, 129, 132 Good, I. J. 116, 129 Greechie, R. J. 71, 129 Greenstein, G. 114, 129 Gribbin, J. 27, 129 Grifﬁths, R. B. 61, 79, 107, 109, 114, 129, 137 Grover, L. K. 115, 129 Gruska, J. 115, 130 Gudder, S. P. 71, 129  

Halmos, P. R. 41, 44, 50, 58, 59, 60, 61, 121, 128, 130 Halpin, J. F. 71, 130 Hardegree, G. M. 35, 37, 38, 40, 63, 64, 66, 69, 70, 71, 130, 132, 135 Harper, W. L. 130, 141 Hartle, J. B. 130 Healey, R. 115, 131, 134 Hearst, M. A. 93, 131 Heelan, P. 71, 72, 131 Heisenberg, W. 113, 115, 131 Hellman, G. 131 Herbut, F. 63, 99, 131 Hiley, B. J. 25, 131 Hirvensalo, M. 115, 131 Holland, S. P. 34, 40, 63, 67, 131 Hooker, C. A. 122, 128, 129, 130, 131, 141 Horn, R. A. 61, 132 Hughes, R. I. G. 3, 12, 18, 19, 49, 71, 80, 109, 125, 129, 132 Huibers, T. 19, 132  

Ingwersen, P. 132 Isham, C. J. 46, 61, 101, 115, 132  

Jauch, J. M. 22, 27, 98, 116, 117, 132, 133 Jaynes, E. T. 116, 124, 125, 133, 134, 143 Jeffrey, R. C. 68, 99, 123, 133 Jeffreys, H. 116, 133 Jordan, T. F. 41, 61, 80, 82, 101, 107, 125, 133, 139  

K¨ agi-Romano, U. 71, 133 Keynes, M. 116, 133 Kochen, S. 71, 131, 133, 134 Kolmogorov, A. N. 133, 134 Korfhage, R. R. 27, 31 Kowalski, G. J. 27, 31, 134 Kyburg, H. E. 93, 134  

Lafferty, J. 98, 125, 134 Lakoff, G. 36, 134 Lavrenko, V. 98, 134 Lewis, D. 64, 68, 70, 71, 125, 134, 136 Lo, H.-K. 115, 135 Lock, P. F. 71, 135 Lockwood, M. 115, 135 Lomonaco, S. J. 49, 115, 135 London, F. 115, 135, 143 L¨ uders, G. 135  

Mackey, G. W. 113, 132, 135 MacLane, S. 40, 101, 122 Marciszewski, W. 29, 31, 40, 135 Maron, M. E. xii, 4, 10, 19, 33, 135 Martinez, S. 99, 136 Melia, J. 124 Mirsky, L. 41, 53, 88, 101, 136 Mittelstaedt, P. 71, 136 Mizzaro, S. 16, 31, 136, 140 Murdoch, D. 115, 136  

Nie, J.-Y. 62, 64, 71, 136 Nielsen, M. A. 78, 80, 84, 96, 115, 136  

Ochs, W. 136 Omn\` es, R. 109, 137  

Packel, E. W. 115, 137 Pais, A. 115, 136, 137 Park, J. L. 81, 137 Parthasarathy, K. R. 76, 79, 98, 118, 125, 137 Pavicic, M. 71, 137 Penrose, R. 27, 80, 81, 135, 137 Peres, A. 109, 137 Petz, D. 79, 137 Pippard, A. B. 138 Piron, C. 71, 72, 138 Pitowsky, I. 71, 119, 138 Pittenger, A. O. 115, 138 Plotnitsky, A. 138 Polkinghorne, J. C. 27, 138 Popper, K. R. 113, 138  

Priest, G. 40, 64, 68, 71, 138 Putnam, H. 71, 121, 123, 128, 138, 141  

Quine, W. V. 36, 96, 138  

Rae, A. 27, 138 Redhead, M. 101, 104, 139 Reed, M. 50, 133, 139 Reichenbach, H. 115, 139, 143 Retherford, J. R. 61, 130, 139 R´ edei, M. 23, 71, 138 Ribeiro-Neto, B. 27, 87, 121 Richman, F. 98, 125, 139 Riesz, F. 50, 74, 139 Robertson, S. E. 16, 20, 139 Rom´ an, L. 72, 139 Roman, S. 61, 101, 139  

Sadun, L. 41, 42, 44, 61, 75, 86, 101, 104, 107, 139 Salton, G. 27, 35, 49, 73, 93, 121, 127, 139 Saracevic, T. 16, 31, 136, 139 Schmeidler, W. 61, 140 Schr¨ odinger, E. 4, 110, 140, 143 Schwarz, H. R. 47, 101, 140 Schwinger, J. 109, 140 Seligman, J. 40, 121 Sibson, R. 38, 140 Simmons, G. F. 47, 73, 101, 140 Sneath, P. H. A. 36, 140 Sneed, J. D. 116, 140 Sober, E. xii, 19, 140  

Sparck Jones, K. 27, 93, 139, 141, 142 Stairs, A. 71, 141 Stalnaker, R. 68, 70, 71, 125, 130, 141 Suppes, P. 71, 109, 117, 141 Sutherland, R. I. 116, 141  

Teller, P. 99, 141 Thomason, R. H. 30, 141 Tombros, A. 93, 141  

Van der Waerden, B. L. 115, 141 Van Fraassen, B. C. 64, 68, 71, 99, 109, 122, 123, 133, 141 Van Rijsbergen, C. J. iii, 14, 27, 31, 32, 34, 35, 38, 62, 68, 70, 71, 83, 89, 93, 94, 96, 97, 98, 99, 100, 120, 121, 122, 124, 125, 134, 142 Varadarajan, V. S. 72, 98, 109, 125, 142 Von Neumann, J. 11, 23, 24, 71, 107, 109, 118, 122, 128, 131, 136, 142 Voorhies, E. M. 93, 143  

Wheeler, J. A. 4, 20, 110, 135, 140, 143 Whitaker, A. 143 Wick, D. 27, 143 Wilkinson, J. H. 58, 61, 143 Williams, D. 119, 143 Witten, I. H. 29, 35, 143 Wootters, W. K. 10, 94, 99, 100, 128, 143, 144  

Zhang, F. 61, 144 Zurek, W. H. 4, 110, 135, 140, 143  

aboutness, ix, 9, 19–22, 32, 33, 93 anti-commutator, 113 artiﬁcial class, 35, 47, 62, 67  

basis 6, 42,  see also  orthonormal basis, canonical basis Bayes’ Theorem, 117 bra, 43, 45, 104  

canonical basis, 74 Cauchy–Schwartz inequality, 46, 107–108, 113 choice disjunction, 66 closure operation, 37 cluster hypothesis, 93, 131, 139, 143 collapse of the wave function, 110–111 column vector, 31, 41, 60 commutative addition, 102 commutative operators, 63 commutativity,  see  commutative addition commutator, 113 compatibility, 33, 66–68 complex conjugate, 44, 55 complex numbers, 5, 24, 25, 44, 74 comprehension axiom, 29 conjugate transpose, 7, 18, 56, 75 content hypothesis, 10 contraposition, 64 co-ordinate transformation, 54 co-ordination level matching, 85–86 cosine correlation, 83, 85, 104 counterfactual conditional, 64 counting measure, 31  

D-notation, 74–79,  see  Dirac notation deduction theorem, 34, 64  

degeneracy, 8, 9 density matrix, 82, 99,  see also  density operator density matrix formalism, 98, 123, 126 density operator, 12, 18, 80–84, 119 Dirac notation, x, xi, 12, 59, 73, 76, 104–105 discounting function, 97 distribution law, xi, 28, 34, 38, 39, 64, 65, 67, 102 dot product,  see  inner product dual space, 12, 84, 96, 104 dyad, 105–106, 137,  see also  outer product dynamic clustering, 91–96  

E-measure, 31, 41 eigenspaces, 9, 17 eigenvalue, 7, 58–59 eigenvector, 8, 58–59 Einstein, A., 2, 139, 141, 143 expectation, 82, 112  

Galois connection, 37, 91 Gleason’s Theorem, 12, 13, 18, 81, 94, 98, 99, 119, 129  

Hahn-Banach Theorem, 47 Heisenberg uncertainty principle, xi, 113–114, 138 Hermitian operator,  see  self-adjoint linear operator Hilbert–Schmidt inner product, 84, 96  

idempotent linear operator, 56 identity matrix, 54 imaging, 70, 100, 125, 134 index term, 3, 19, 20, 39  

inner product, 5, 6, 9, 21, 23, 43, 45, 74, 80, 84, 103, 104 interaction logic, 22, 142 interaction protocol, 22 inverted ﬁle, 35, 91  

Jeffrey conditional is ation, 99, 123, 133  

Kant, I., 101 ket, 45, 74, 104 keyword,  see  index term Kolmogorov axioms, 25, 116, 134  

language modelling, 93, 98, 99, 125, 134 latent semantic analysis, 10 latent semantic indexing, 23, 86 lattice,  see  ortho complemented lattice, orthomodular lattice linear functional, 74, 104 linearly dependent, 42 linearly independent, 5, 42 logical uncertainty principle (LUP), 93, 98, 100, 142  

Maron and Kuhns, 141 material conditional, 64, 138 matrix,  see  identity matrix, metric matrix, zero matrix matrix multiplication, 53, 78, 107 Maxwell, J. C., 116 measurement problem, 124, 136, 143 metric, 46, 92 metric matrix, 86 modus ponens, 64 monothetic kinds, 37, 38  

natural kinds, 35, 37 negative probability, 25 non-Boolean lattice, xi, 11, 118 non-Boolean logic, xi, 35 non-commutative operators, 22, 52, 106, 113 non-singular transformation, 52 norm, 45  

observable, 3, 7, 18, 19, 63, 91, 99, 110–111 ortho complemented lattice, 66 orthogonality, 5, 9, 23, 46, 56, 59, 65, 88, 90, 91 orthomodular lattice, 63, 131 orthomodular law, 66 orthonormal basis, 19, 46 ostensive model, 14, 124  

ostensive retrieval, 13, 96–98, 99 outer product, 75  

Plato, 73 polythetic kinds, 38 principle of compositional it y, 30 probabilistic indexing, 4, 10, 14 probability measure, 116–117 probability of relevance, 16, 92, 96 precision, 31 projector, 8, 10, 56–58, 112, 119 projection,  see  projector projection operator,  see  projector projective geometry, 23, 78 pseudo-relevance feedback, 87–89 Pythagoras’ Theorem, 9, 18, 25  

quantum computation, x, 1, 115, 126, 130, 135, 136, 137, 138, 143 quantum logic, 3, 49, 119, 121, 122, 129 quantum mechanics glossary, 129 quantum probability, 117–119 question-valued measure, 112–113  

ray, 74 recall, 31 relevance, 15, 16, 17, 32, 67 relevance feedback, iii, 89–91 resolution of unity, 76 retrieval effectiveness, 31–32 row vector, 45, 60  

S-conditional,  see  subspace conditional, sandwich notation, 105 Schmidt orthogonal is ation process, 47–49 Schr¨ odinger, 3, 4, 141 Schr¨ odinger equation, 114 selection function, 68 self-adjoint linear operator, 7, 8, 17, 55, 62, 99, 103, 110, 127, 139 semantic gap, 20 span, 47, 118 Spectral Theorem, 59–60, 61, 63 Stalnaker conditional, 68–70, 125 state vector, 4, 17, 114, 126 Stone Representation Theorem, 29, 39, 117 subspace closure, 47 subspace conditional, 64  

trace, 12, 79–80, 83–84, 118 trace class, 81 transitivity, 64  

transpose, 43, 45, 55 triangle inequality, 46, 92  

ultrametric inequality, 92 unit vector, 45  

vector,  see  column vector, row vector, unit vector, zero vector Von Neumann, J., xii, 2, 3, 4, 11, 23, 111, 124, 131, 138  

Von Neumann’s projection postulate, 7, 8, 99, 110  

yes/no questions, 8, 10, 20, 22, 59, 71, 112, 122, 132  

zero matrix, 54 zero vector, 42, 43  