---
title: CoNLL-U annotation Test
keywords:
tags:
sidebar: home_sidebar
permalink: conllu.html
summary:
---
## CoNLL-U preliminary testing

CoNLL-U implementation based on: <http://universaldependencies.org/format.html>

Original CoNLL-U Syntax calls for such structure marking:

	# newdoc id = mf920901-001
	# newpar id = mf920901-001-p1
	# sent_id = mf920901-001-p1s1A
	# text = Slovenská ústava: pro i proti
	# text_en = Slovak constitution: pros and cons

In the Ur III administrative corpus, sentences span many lines and the structure of documents is complex and is divided into surfaces and sections, based on the medium of the text. The ConLL-U syntax is thus adapted as such:

	# newdoc id = P101049
	# newsurface id = P101049-obverse
	# newsection id = P101049-obverse-column-001
	# line_id = P101049-obverse-column-001-0001
	# text = 2(disz) ma2 1(gesz2) gur 2(ban2)-ta ma2-lah5-bi i3-ib2-u3
	# text_en = 2 barges of 60 gur (capacity), 2 ban2 (per day) each, their skippers piloting

Notes: It might be best to reduce the ids to the actual division and process the preceding divisions to get their ids if needed, to avoid repetition? Eg:

	# newdoc id = P101049
	# newsurface id = obverse
	# newsection id = column 1
	# line_id = 1
	# text = 2(disz) ma2 1(gesz2) gur 2(ban2)-ta ma2-lah5-bi i3-ib2-u3
	# text_en = 2 barges of 60 gur (capacity), 2 ban2 (per day) each, their skippers piloting

## ConLL-U Fields  
- ID: Word index, integer starting at 1 for each new sentence; may be a range for multiword tokens; may be a decimal number for empty nodes.  
- FORM: Word form or punctuation symbol.  
- LEMMA: Lemma or stem of word form.  
- UPOSTAG: Universal Dependencies (UD) part-of-speech tag.  
- XPOSTAG: Language-specific part-of-speech tag; underscore if not available.  
- FEATS: List of morphological features from the universal feature inventory or from a defined language-specific extension; underscore if not available.  
- HEAD: Head of the current word, which is either a value of ID or zero (0).  
- DEPREL: Universal dependency relation to the HEAD (root iff HEAD = 0) or a defined language-specific subtype of one.  
- DEPS: Enhanced dependency graph in the form of a list of head-deprel pairs.  
- MISC: Any other annotation.  

HEAD, DEPREL, and DEPS will be used only when we get to syntactic parsing and we should be able to use the Bratt GUI editor for this task. (http://brat.nlplab.org/)

In the examples below, the UPOSTAG field is completed using UD and XPOSTAG with ORACC/ETCSL/PENN so we can compare the different tag sets available.

The FEATS field displays tags as:  UD / ETCSRI. ETCSL tags will be added when available


WORK IN PROGRESS

## P101049
<http://cdli.ucla.edu/P101049>

	# newdoc id = P101049
	# newsurface id = obverse

	# line_id = 1
	# text = 2(disz) ma2 1(gesz2) gur 2(ban2)-ta ma2-lah5-bi i3-ib2-u3
	# text_en = 2 barges of 60 gur (capacity), 2 ban2 (per day) each, their skippers piloting
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	2(disz)	2(disz)	NUM	NU/NU/CD	X	_	_	_	_
	2	ma2	ma2	NOUN	N/N/NNS	X	_	_	_	_
	3	1(gesz2)	1(gesz2)	NUM	NU/NU/CD	X	_	_	_	_
	4	gur	gur	NOUN	N/N/NNS	X	_	_	_	_
	5	2(ban2)-ta	2(ban2)	NUM	NU/NU/CD	X	_	_	_	_
	6	ma2-lah5-bi	ma2-lah5	NOUN	N/N/NNS	X	_	_	_	_
	7	i3-ib2-u3	u3	VERB	V/V/VB	X	_	_	_	_

	# line_id = 2
	# text = u4 3(u) 2(disz)-sze3
	# text_en =  for 32 days,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	u4	u4	NOUN	N/N/NNS	X	_	_	_	_
	2	3(u)	3(u)	NUM	NU/NUM/CD	X	_	_	_	_
	3	2(disz)-sze3	2(disz)	NUM	NU/NU/CD	X	_	_	_	_

	# line_id = 3
	# text = sze-bi 4(asz) 1(barig) 2(ban2) gur
	# text_en =  its barley: 4 gur 1 barig 2 ban2;
	# calculation: 32 × 2 × 0;0,2 = 4;1,2
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sze-bi	 sze	NOUN	N/N/NN	X	_	_	_	_
	2	4(asz)	4(asz)	NUM	NU/NU/CD	X	_	_	_	_
	3	1(barig)	1(barig)	NUM	NU/NU/CD	X	_	_	_	_
	4	2(ban2)	2(ban2)	NUM	NU/NU/CD	X	_	_	_	_
	5	gur	gur	NOUN	N/N/NNS	X	_	_	_	_

	# newsurface id = reverse

	# line_id = 1
	# text = a-pi4-sal4{ki}-ta
	# text_en =  from Apisal
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	a-pi4-sal4{ki}-ta	a-pi4-sal4{ki}	PROPN	GN/GN/NNP	X	_	_	_	_

	# line_id = 2
	# text = nibru{ki}-sze3 siki ba-a-si
	# text_en = to Nippur, with wool filled,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	nibru{ki}-sze3	nibru{ki}	PROPN	GN/GN/NNP	X	_	_	_	_
	2	siki	siki	NOUN	N/N/NN	X	_	_	_	_
	3	ba-a-si	si	VERB	V/V/VB	X	_	_	_	_

	# line_id = 3
	# text = giri3 ur-e11-e
	# text_en = via Ur-e’e,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	giri3	giri3	PRP/?/IN	ADP	X	_	_	_	_
	2	ur-e11-e	ur-e11-e	PROPN	PN/PN/NNP	X	_	_	_	_

	# line_id = 4
	# text = mu ur-bi2-lum{ki} ba-hul
	# text_en = year: Urbilum was destroyed.
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	mu	mu	NOUN	N/N/NN	X	_	_	_	_
	2	ur-bi2-lum{ki}	ur-bi2-lum{ki}	PROPN	GN/GN/NNP	X	_	_	_	_
	3	ba-hul	hul	VERB	V/V/VB	X	_	_	_	_



## P427604
<http://cdli.ucla.edu/P427604>

	# newdoc id = P427604
	# newsurface id = obverse

	# line_id = 1
	# text = 1(disz) szah2-ze2-da
	# text_en = 1 piglet
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	NUM     	NU/NU/CD	_	_	_	_	_
	2	szah2-ze2-da	szah2-ze2-da	NOUN	N/N/NN	_	_	_	_	_
_	_	_	_	_
	# line_id = 2
	# text = iti u4 1(disz) ba-zal
	# text_en = of the month, 1st day passed;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	iti	iti	NOUN	N/N/NN	_	_	_	_	_
	2	u4	u4	NOUN	N/N/NNS	_	_	_	_	_
	3	1(disz)	1(disz)	NUM	NU/NU/CD	_	_	_	_	_
	4	ba-zal	zal	VERB	V/V/VB	_	_	_	_	_

	# line_id = 3
	# text = 1(disz) udu niga
	# text_en = 1 grain-fed sheep,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	NUM	NU/NU/CD	_	_	_	_	_
	2	udu	udu	NOUN	N/N/NN	_	_	_	_	_
	3	niga	niga	ADJ	AJ/AJ/JJ	_	_	_	_	_

	# line_id = 4
	# text = iti u4 1(u) ba-zal
	# text_en = of the month, 10th day passed;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	iti	iti	NOUN	N/N/NN	_	_	_	_	_
	2	u4	u4	NOUN	N/N/NNS	_	_	_	_	_
	3	1(u)	1(u)	NUM	NU/NU/CD	_	_	_	_	_
	4	ba-zal	zal	VERB	V/V/VB	_	_	_	_	_

	# line_id = 5
	# text = 1(disz) szah2-ze2-da
	# text_en = 1 piglet
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	NUM	NU/NU/CD	_	_	_	_	_
	2	szah2-ze2-da	szah2-ze2-da	NOUN	N/N/NNS	_	_	_	_	_

	# line_id = 6
	# text = iti u4 1(u) 5(disz) ba-zal
	# text_en = of the month, 15th day passed
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	iti	iti	NOUN	N/N/NN	_	_	_	_	_
	2	u4	u4	NOUN	N/N/NNS	_	_	_	_	_
	3	1(u)	1(u)	NUM	NU/NU/CD	_	_	_	_	_
	4	5(disz)	5(disz)	NUM	NU/NU/CD	_	_	_	_	_
	5	ba-zal	zal	VERB	V/V/VB	_	_	_	_	_

	# line_id = 7
	# text = 1(disz) udu niga
	# text_en = 1 grain-fed sheep
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	NUM	NU/NU/CD	_	_	_	_	_
	2	udu	udu	NOUN	N/N/NN	_	_	_	_	_
	3	niga	niga	ADJ	AJ/AJ/JJ	_	_	_	_	_

	# line_id = 8
	# text = iti u4 2(u) ba-zal
	# text_en = of the month, 20th day passed;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	iti	iti	NOUN	N/N/NN	_	_	_	_	_
	2	u4	u4	NOUN	N/N/NN	_	_	_	_	_
	3	2(u)	2(u)	NUM	NU/NU/CD	_	_	_	_	_
	4	ba-zal	zal	VERB	V/V/VB	_	_	_	_	_

	# line_id = 9
	# text = 1(disz)# udu# [niga]
	# text_en = 1 grain-fed sheep,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	NUM	NU/NU/CD	_	_	_	_	_
	2	udu	udu	NOUN	N/N/NN	_	_	_	_	_
	3	niga	niga	ADJ	AJ/AJ/JJ	_	_	_	_	_

	# line_id = 10
	# text = [iti u4 2(u) 8(disz) ba-zal]
	# text_en = of the month, 28th day passed
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	iti	iti	NOUN	N/N/NN	_	_	_	_	_
	2	u4	u4	NOUN	N/N/NNS	_	_	_	_	_
	3	2(u)	2(u)	NUM	NU/NU/CD	_	_	_	_	_
	4	8(disz)	8(disz)	NUM	NU/NU/CD	_	_	_	_	_
	5	ba-zal	zal	VERB	V/V/VB	_	_	_	_	_

	# newsurface id = reverse

	# line_id = 1
	# text = sa2-du11 ki-a-nag# [szu-kab-ta2]
	# text_en = rations of the libation place of Šukabta,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sa2-du11	sa2-du11	NOUN	N/N/NN	_	_	_	_	_
	2	ki-a-nag	ki-a-nag	NOUN	N/N/NN	_	_	_	_	_
	3	szu-kab-ta2	szu-kab-ta2	PROPN	GN/GN/NNP	_	_	_	_	_

	# line_id = 2
	# text = ki {d}iszkur-illat-ta
	# text_en = out of Adad-tillati(’s account)
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	ki	ki	PRP/?/IN	ADP	_	_	_	_	_
	2	{d}iszkur-illat-ta	{d}iszkur-illat-ta	PROPN	PN/PN/NNP	_	_	_	_	_

	# line_id = 3
	# text = ba-zi
	# text_en = booked;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	ba-zi	zi	VERB	V/V/VB	_	0	root	0:root	_

	# line_id = 4
	# text = sza3 gar-sza-an-na{ki}
	# text_en = in Garšana
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sza3	sza3	PRP/?/IN	ADP	_	_	_	_	_
	2	gar-sza-an-na{ki}	gar-sza-an-na{ki}	PROPN	GN/GN/NNP	_	_	_	_	_

	# line_id = 5
	# text = iti ezem-{d}nin-a-zu
	# text_en = month “Festival of Ninazu”
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	iti	iti	NOUN	N/N/NN	_	_	_	_	_
	2	ezem-{d}nin-a-zu	ezem-{d}nin-a-zu	PROPN	MN/MN/NNP	_	_	_	_	_

	# line_id = 6
	# text = mu {d}szu-{d}suen lugal uri5{ki}-ma-[ke4] e2 {d}szara2 umma{ki}-ka mu-[du3]
	# text_en = year: “Šu-Suen, king of Ur, the house of Šara in Umma erected;”
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	mu	mu	NOUN	N/N/NN	_	_	_	_	_
	2	{d}szu-{d}suen	{d}szu-{d}suen	PROPN	PN/PN/NNP	_	_	_	_	_
	3	lugal	lugal	NOUN	N/N/NN	_	_	_	_	_
	4	uri5{ki}-ma-ke4	uri5{ki}	PROPN	GN/GN/NNP	_	_	_	_	_
	5	e2	e2	NOUN	N/N/NN	_	_	_	_	_
	6	{d}szara2	{d}szara2	PROPN	DN/DN/NNP	_	_	_	_	_
	7	umma{ki}-ka	umma{ki}	PROPN	GN/GN/NNP	_	_	_	_	_
	8	mu-du3	du3	VERB	V/V/VB	_	0	root	0:root	_

	# newsurface id = left

	# line_id = 1
	# text = gaba-ri
	# text_en = copy
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	gaba-ri	gaba-ri	NOUN	N/N/NN	_	_	_	_	_


	## P102359
	<http://cdli.ucla.edu/P102359>

	# newdoc id = P102359
	# newsurface id = obverse

	# line_id = 1
	# text = 1(u) 1(disz) kusz gu4 niga
	# text_en = 11 ox-hides, grain-fed
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(u)	1u	_	_	_	_	_
	2	1(disz)	1disz	_	_	_	_	_
	3	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	4	gu4	gu4	_	_	_	_	_
	5	niga	niga	_	_	_	_	_

	# line_id = 2
	# text = 7(gesz2) 3(u) la2 1(disz) kusz udu
	# text_en = 429 sheep-hides,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	7(gesz2)	7(gesz2)	_	_	_	_	_
	2	3(u)	3(u)	_	_	_	_	_
	3	la2	la2	_	_	_	_	_
	4	1(disz)	1(disz)	_	_	_	_	_
	5	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	6	udu	udu	_	_	_	_	_

	# line_id = 3
	# text = 2(disz) kusz sila4
	# text_en = 2 lamb-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	2(disz)	2(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	sila4	sila4	_	_	_	_	_

	# line_id = 4
	# text = sa2-du11 {d}szara2 umma{ki}
	# text_en = regular offerings of Šara of Umma
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sa2-du11	sa2-du11	NOUN	N/N/NNS	_	_	_	_	_
	2	{d}szara2	{d}szara2	_	_	_	_	_
	3	 umma{ki}	 umma{ki}	_	_	_	_	_

	# line_id = 5
	# text =1(disz) kusz gu4 niga 2(disz) kusz udu niga
	# text_en = 1 ox-hide, grain-fed, 2 sheep-hides, grain-fed
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	gu4	gu4	_	_	_	_	_
	4	niga	niga	_	_	_	_	_
	5	2(disz)	2(disz)	_	_	_	_	_
	6	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	7	udu	udu	_	_	_	_	_
	8	niga	niga	_	_	_	_	_

	# line_id = 6
	# text = 3(u) 7(disz) kusz udu
	# text_en = 37 sheep-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	3(u)	3(u)	_	_	_	_	_
	2	7(disz)	7(disz)	_	_	_	_	_
	3	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	4	udu	udu	_	_	_	_	_

	# line_id = 7
	# text = sa2-du11 {d}szara2 |KI.AN|[{ki}]
	# text_en =	regular offerings of Šara of KI.AN;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sa2-du11	sa2-du11	NOUN	N/N/NNS	_	_	_	_	_
	2	{d}szara2	{d}szara2	_	_	_	_	_
	3	|KI.AN|{ki}	|KI.AN|{ki}	_	_	_	_	_

	# line_id = 8
	# text = 4(u) 7(disz) kusz udu niga 3(u) kusz sila4
	# text_en =	47 sheep-hides, grain-fed, 30 lamb-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	4(u)	4(u)	_	_	_	_	_
	2	7(disz)	7(disz)	_	_	_	_	_
	3	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	4	udu	udu	_	_	_	_	_
	5	niga	niga	_	_	_	_	_
	6	3(u)	3(u)	_	_	_	_	_
	7	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	8	sila4	sila4	_	_	_	_	_

	# text =nig2-{gesz}tag-ga# [lugal]
	# text_en = royal sacrifice
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	nig2-{gesz}tag-ga	nig2-{gesz}tag-ga	_	_	_	_	_
	2	lugal	lugal	_	_	_	_	_

	# line_id = 10
	# text = 1(disz) kusz gu4 niga
	# text_en =  1 ox-hide, grain-fed
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	gu4	gu4	_	_	_	_	_
	4	niga	niga	_	_	_	_	_

	# line_id = 11
	# text = 1(gesz2) la2 2(disz) kusz udu niga
	# text_en = 58 sheep-hides, grain-fed
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(gesz2)	1(gesz2)	_	_	_	_	_
	2	la2	la2	_	_	_	_	_
	3	2(disz)	2(disz)	_	_	_	_	_
	4	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	5	udu	udu	_	_	_	_	_
	6	niga	niga	_	_	_	_	_

	# line_id = 12
	# text = 3(u) 2(disz) kusz udu
	# text_en = 32 sheep-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	3(u)	3(u)	_	_	_	_	_
	2	2(disz)	2(disz)	_	_	_	_	_
	3	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	4	udu	udu	_	_	_	_	_

	# line_id = 13
	# text = sza3 sa2-du11 [(x)]
	# text_en = in the regular offerings ...
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sza3	sza3	_	_	_	_	_
	2	sa2-du11	sa2-du11	NOUN	N/N/NNS	_	_	_	_	_
	3	x	x	_	_	_	_	_

	# line_id = 14
	# text = 1(u) 2(disz) kusz masz2
	# text_en = 12 billy goat-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(u)	1(u)	_	_	_	_	_
	2	2(disz)	2(disz)	_	_	_	_	_
	3	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	4	masz2	masz2	_	_	_	_	_

	# line_id = 15
	# text = sa2-du11 dah-ha {d}szul-gi
	# text_en = regular offerings, additional, of Šulgi
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sa2-du11	sa2-du11	_	_	_	_	_
	2	dah-ha	dah-ha	_	_	_	_	_
	3	{d}szul-gi	{d}szul-gi	_	_	_	_	_

	# line_id = 16
	# text = 5(u) kusz udu 2(u) 1(disz) kusz sila4
	# text_en = 50 sheep-hides, 21 lamb-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	5(u)	5(u)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	2(u)	2(u)	_	_	_	_	_
	5	1(disz)	1(disz)	_	_	_	_	_
	6	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	7	sila4	sila4	_	_	_	_	_

	# line_id = 17
	# text = {d}nin-ur4-ra
	# text_en = for Ninura
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}nin-ur4-ra	{d}nin-ur4-ra	_	_	_	_	_

	# line_id = 18
	# text = 1(u) kusz udu 7(disz) kusz sila4
	# text_en = 10 sheep-hides, 7 lamb-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(u)	1(u)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	7(disz)	7(disz)	_	_	_	_	_
	5	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	6	sila4	sila4	_	_	_	_	_

	# newsurface id = reverse

	# line_id = 1
	# text = 	{d}eb-gal
	# text_en = (for) Ebgal
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}eb-gal	{d}eb-gal	_	_	_	_	_

	# line_id = 2
	# text = 1(u) kusz udu 8(disz) kusz sila4
	# text_en = 1 sheep-hide, 8 lamb-hides,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(u)	1(u)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	8(disz)	8(disz)	_	_	_	_	_
	5	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	6	sila4	sila4	_	_	_	_	_

	# line_id = 3
	# text = {d}en-lil2
	# text_en = (for) Enlil;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}en-lil2	{d}en-lil2	_	_	_	_	_
	_	_	_	_	_

	# line_id = 4
	# text = 1(disz) kusz udu {d}nansze <umma>{ki}
	# text_en = 1 sheep-hides (for) Nanše of Umma;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	{d}nansze	{d}nansze	_	_	_	_	_
	5	umma{ki}	umma{ki}	_	_	_	_	_

	# line_id = 5
	# text = 1(disz) kusz udu {d}gu-la [(x)]
	# text_en = 1 sheep-hide for Gula;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	1(disz)	1(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	{d}gu-la	{d}gu-la	_	_	_	_	_
	5	x	x	_	_	_	_	_

	# line_id = 6
	# text = 3(u) 1(disz) kusz udu 2(u) kusz [x]
	# text_en = 30 sheep-hides, 20 ...-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	3(u)	3(u)	_	_	_	_	_
	2	1(disz)	1(disz)	_	_	_	_	_
	3	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	4	udu	udu	_	_	_	_	_
	5	2(u)	2(u)	_	_	_	_	_
	6	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	7	x	x	_	_	_	_	_

	# line_id = 7
	# text = {d}inanna zabala{ki} [{d}nin]-ildu3#-ma u3 {d}ku3-[sig17-banda3{da}]
	# text_en = for Innana of Zabala, Nin-ilduma and Kusig-banda
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}inanna	{d}inanna	_	_	_	_	_
	2	zabala{ki}	zabala{ki}	_	_	_	_	_
	3	{d}nin-ildu3-ma	{d}nin-ildu3-ma	_	_	_	_	_
	4	u3	u3	_	_	_	_	_
	5	{d}ku3-sig17-banda3{da}	{d}ku3-sig17-banda3{da}	_	_	_	_	_

	# line_id = 8
	# text = 3(disz) kusz udu ensi2 x [...]
	# text_en = 3 sheep-hides, for the governor of ...
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	3(disz)	3(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	ensi2	ensi2	_	_	_	_	_
	5	x	x	_	_	_	_	_
	6	...	...	_	_	_	_	_

	# line_id = 9
	# text = 6(disz) kusz udu 4(disz) kusz [...]
	# text_en = 6 sheep-hides, 4 ...-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	6(disz)	6(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	4(disz)	4(disz)	_	_	_	_	_
	5	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	6	...	...	_	_	_	_	_

	# line_id = 10
	# text = {d}e11-[e?] x [x]
	# text_en = for E’e ...;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}e11-[e?]	{d}e11-[e?]	_	_	_	_	_
	2	x	x	_	_	_	_	_
	3	x	x	_	_	_	_	_

	# line_id = 11
	# text = 4(disz) kusz udu 2(disz) [kusz x]
	# text_en =  4 sheep-hides, 2 ...-hides,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	4(disz)	4(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	2(disz)	2(disz)	_	_	_	_	_
	5	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	6	x	x	_	_	_	_	_

	# line_id = 12
	# text = {d}da-lagasz#[{ki}]
	# text_en = for Da-Lagaš;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}da-lagasz{ki}	{d}da-lagasz{ki}	_	_	_	_	_

	# line_id = 13
	# text =8(disz) kusz udu 4(disz) kusz sila4
	# text_en = 8 sheep-hides, 4 lamb-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	8(disz)	8(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	4(disz)	4(disz)	_	_	_	_	_
	5	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	6	sila4	sila4	_	_	_	_	_

	# line_id = 14
	# text = {d}en-ki u3 {d}USZ#-ka-limmu5
	# text_en = for Enki and UŠkalimmu;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}en-ki	{d}en-ki	_	_	_	_	_
	2	u3	u3	_	_	_	_	_
	3	{d}USZ-ka-limmu5	{d}USZ-ka-limmu5	_	_	_	_	_

	# line_id = 15
	# text = 4(disz) kusz udu 2(disz) kusz sila4
	# text_en = 4 sheep-hides, 2 lamb-hides
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
		 	1	4(disz)	4(disz)	_	_	_	_	_
	2	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	3	udu	udu	_	_	_	_	_
	4	2(disz)	2(disz)	_	_	_	_	_
	5	kusz	kusz	NOUN	N/N/NNS	_	_	_	_	_
	6	sila4	sila4	_	_	_	_	_

	# line_id = 16
	# text =	{d}dumu-zi iri-min
	# text_en =	for Dumuzi of double-city;
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	{d}dumu-zi	{d}dumu-zi	_	_	_	_	_
	2	iri-min	iri-min	_	_	_	_	_

	# line_id = 17
	# text = sa2-du11 dingir-e-ne
	# text_en = regular offerings of the gods
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	sa2-du11	sa2-du11	NOUN	N/N/NNS	_	_	_	_	_
	2	dingir-e-ne	dingir	NOUN	N/N/NNS	_	_	_	_	_

	# line_id = 18
	# text = mu us2-sa bad3 ba-du3
	# text_en = year after: The wall was erected.
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	mu	mu	_	_	_	_	_
	2	us2-sa	us2-sa	_	_	_	_	_
	3	bad3	bad3	_	_	_	_	_
	4	ba-du3	du3	VERB	V/V/VB	morph	_	_	_	_

*Émilie Pagé-Perron*
