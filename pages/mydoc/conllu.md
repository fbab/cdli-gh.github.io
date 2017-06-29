
# MTAAC CoNLL-U preliminary testing

Based on: http://universaldependencies.org/format.html

Original CoNLL-U Syntax calls for such structure marking:
	# newdoc id = mf920901-001
	# newpar id = mf920901-001-p1
	# sent_id = mf920901-001-p1s1A
	# text = Slovenská ústava: pro i proti
	# text_en = Slovak constitution: pros and cons

In the Ur III administrative corpus, sentences span many lines and the structure of documents is complex and is divided into surfaces and sections. The ConLL-U syntax is thus adapted as such:

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
- UPOSTAG: Universal part-of-speech tag.  
- XPOSTAG: Language-specific part-of-speech tag; underscore if not available.  
- FEATS: List of morphological features from the universal feature inventory or from a defined language-specific extension; underscore if not available.  
- HEAD: Head of the current word, which is either a value of ID or zero (0).  
- DEPREL: Universal dependency relation to the HEAD (root iff HEAD = 0) or a defined language-specific subtype of one.  
- DEPS: Enhanced dependency graph in the form of a list of head-deprel pairs.  
- MISC: Any other annotation.  

HEAD, DEPREL, and DEPS will be used only when we get to syntactic parsing and we should be able to use the Bratt GUI editor for this task. (http://brat.nlplab.org/)

In the examples below, the UPOSTAG field is completed using UD and XPOSTAG with ORACC/ETCSL/PENN so we can compare the different tag sets available.

The FEATS field displays tags as:  UD / ETCSRI. I hope to be able to add the ETCSL tags soon.

## P101049
	# newdoc id = P101049
	# newsurface id = obverse
	# line_id = 1
	# text = 2(disz) ma2 1(gesz2) gur 2(ban2)-ta ma2-lah5-bi i3-ib2-u3
	# text_en = 2 barges of 60 gur (capacity), 2 ban2 (per day) each, their skippers piloting

	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	2(disz)	2disz	NUM	NU/NU/CD	X	-	-	-	-
	2	ma2	ma2	NOUN	N/N/NNS	X	 -	-	-	-
	3	1(gesz2)	1gesz2	NUM	NU/NU/CD	X	-	-	-	-
	4	gur	gur	NOUN	N/NNS	X	-	-	-	-
	5	2(ban2)-ta	2ban2	NUM	NU/NU/CD	X	-	-	-	-
	6	ma2-lah5-bi	ma2-lah5	X	X	X	-	-	-	-
	7	i3-ib2-u3	VERB	V/V/	X	X	-	-	-	-

	# line_id = 2
	# text = u4 3(u) 2(disz)-sze3
	# text_en =  for 32 days,
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
	1	u4	u4	NOUN	N/N/NNS	X	-	-	-	-
	2	3(u)	3u	NUM	NU/NUM/CD	X	-	-	-	-
	3	2(disz)-sze3	2disz	NUM	NU/NU/CD	X	-	-	-	-

	# line_id = 3
	# text = sze-bi 4(asz) 1(barig) 2(ban2) gur
	# text_en =  its barley: 4 gur 1 barig 2 ban2;
	# calculation: 32 × 2 × 0;0,2 = 4;1,2
	#ID FORM  LEMMA UPOSTAG XPOSTAG FEATS HEAD  DEPREL  DEPS  MISC
	1	sze-bi X X X X - - - -
	2	4(asz) 4asz NUM NU/NU/CD	X	X	X	X	-	-	-	-
	3	1(barig) 1barig NUM NU/NU/CD	X	X	X	X	-	-	-	-
	4	2(ban2) 2ban2 NUM NU/NU/CD	X	X	X	X	-	-	-	-
	5	gur gur NOUN  N/N/NN X X	X	X	X	X	-	-	-	-

	# newsurface id = reverse
	# line_id = 1
	# text = a-pi4-sal4{ki}-ta
	# text_en =  from Apisal
	ID FORM  LEMMA UPOSTAG XPOSTAG FEATS HEAD  DEPREL  DEPS  MISC
	1	a-pi4-sal4{ki}-ta	X	X	X	X	-	-	-	-

	# line_id = 2
	# text = nibru{ki}-sze3 siki ba-a-si
	# text_en = to Nippur, with wool filled,
	#ID FORM  LEMMA UPOSTAG XPOSTAG FEATS HEAD  DEPREL  DEPS  MISC
	1	nibru{ki}-sze3	X	X	X	X	-	-	-	-
	2	siki	X	X	X	X	-	-	-	-
	3	ba-a-si	X	X	X	X	-	-	-	-

	# line_id = 3
	# text = giri3 ur-e11-e
	# text_en = via Ur-e’e,
	#ID FORM  LEMMA UPOSTAG XPOSTAG FEATS HEAD  DEPREL  DEPS  MISC
	1	giri3	X	X	X	X	-	-	-	-
	2	ur-e11-e	X	X	X	X	-	-	-	-

	# line_id = 4
	# text = mu ur-bi2-lum{ki} ba-hul
	# text_en = year: Urbilum was destroyed.
	#ID FORM  LEMMA UPOSTAG XPOSTAG FEATS HEAD  DEPREL  DEPS  MISC
	1	mu	X	X	X	X	-	-	-	-
	2	ur-bi2-lum{ki}	X	X	X	X	-	-	-	-
	3	ba-hul	X	X	X	X	-	-	-	-


&P101049 = AnOr 01, 058
#atf: lang sux
@tablet
@obverse
1. 2(disz) ma2 1(gesz2) gur 2(ban2)-ta ma2-lah5-bi i3-ib2-u3
#tr.en: 2 barges of 60 gur (capacity), 2 ban2 (per day) each, their skippers piloting,
2. u4 3(u) 2(disz)-sze3
#tr.en: for 32 days,
3. sze-bi 4(asz) 1(barig) 2(ban2) gur
#tr.en: its barley: 4 gur 1 barig 2 ban2;
# calculation: 32 × 2 × 0;0,2 = 4;1,2
@reverse
1. a-pi4-sal4{ki}-ta
#tr.en: from Apisal
2. nibru{ki}-sze3 siki ba-a-si
#tr.en: to Nippur, with wool filled,
3. giri3 ur-e11-e
#tr.en: via Ur-e’e,
4. mu ur-bi2-lum{ki} ba-hul
#tr.en: year: “Urbilum was destroyed.”
# Šulgi 45

# sent_id 1
1	&P101049	_	_	_	_	_	_	_	_
2	=	_	_	_	_	_	_	_	_
3	AnOr	_	_	_	_	_	_	_	_
4	01,	_	_	_	_	_	_	_	_
5	058	_	_	_	_	_	_	_	_
6	#atf:	_	_	_	_	_	_	_	_
7	lang	_	_	_	_	_	_	_	_
8	sux	_	_	_	_	_	_	_	_
9	@tablet	_	_	_	_	_	_	_	_
10	@obverse	_	_	_	_	_	_	_	_
11	1.	_	_	_	_	_	_	_	_

# sent_id 2
1	2(disz)	_	_	_	_	_	_	_	_
2	ma2	_	_	_	_	_	_	_	_
3	1(gesz2)	_	_	_	_	_	_	_	_
4	gur	_	_	_	_	_	_	_	_
5	2(ban2)-ta	_	_	_	_	_	_	_	_
6	ma2-lah5-bi	_	_	_	_	_	_	_	_
7	i3-ib2-u3	_	_	_	_	_	_	_	_
8	#tr.en:	_	_	_	_	_	_	_	_
9	2	_	_	_	_	_	_	_	_
10	barges	_	_	_	_	_	_	_	_
11	of	_	_	_	_	_	_	_	_
12	60	_	_	_	_	_	_	_	_
13	gur	_	_	_	_	_	_	_	_
14	(capacity),	_	_	_	_	_	_	_	_
15	2	_	_	_	_	_	_	_	_
16	ban2	_	_	_	_	_	_	_	_
17	(per	_	_	_	_	_	_	_	_
18	day)	_	_	_	_	_	_	_	_
19	each,	_	_	_	_	_	_	_	_
20	their	_	_	_	_	_	_	_	_
21	skippers	_	_	_	_	_	_	_	_
22	piloting,	_	_	_	_	_	_	_	_
23	2.	_	_	_	_	_	_	_	_

# sent_id 3
1	u4	_	_	_	_	_	_	_	_
2	3(u)	_	_	_	_	_	_	_	_
3	2(disz)-sze3	_	_	_	_	_	_	_	_
4	#tr.en:	_	_	_	_	_	_	_	_
5	for	_	_	_	_	_	_	_	_
6	32	_	_	_	_	_	_	_	_
7	days,	_	_	_	_	_	_	_	_
8	3.	_	_	_	_	_	_	_	_

# sent_id 4
1	sze-bi	_	_	_	_	_	_	_	_
2	4(asz)	_	_	_	_	_	_	_	_
3	1(barig)	_	_	_	_	_	_	_	_
4	2(ban2)	_	_	_	_	_	_	_	_
5	gur	_	_	_	_	_	_	_	_
6	#tr.en:	_	_	_	_	_	_	_	_
7	its	_	_	_	_	_	_	_	_
8	barley:	_	_	_	_	_	_	_	_
9	4	_	_	_	_	_	_	_	_
10	gur	_	_	_	_	_	_	_	_
11	1	_	_	_	_	_	_	_	_
12	barig	_	_	_	_	_	_	_	_
13	2	_	_	_	_	_	_	_	_
14	ban2;	_	_	_	_	_	_	_	_
15	#	_	_	_	_	_	_	_	_
16	calculation:	_	_	_	_	_	_	_	_
17	32	_	_	_	_	_	_	_	_
18	×	_	_	_	_	_	_	_	_
19	2	_	_	_	_	_	_	_	_
20	×	_	_	_	_	_	_	_	_
21	0;0,2	_	_	_	_	_	_	_	_
22	=	_	_	_	_	_	_	_	_
23	4;1,2	_	_	_	_	_	_	_	_
24	@reverse	_	_	_	_	_	_	_	_
25	1.	_	_	_	_	_	_	_	_

# sent_id 5
1	a-pi4-sal4{ki}-ta	_	_	_	_	_	_	_	_
2	#tr.en:	_	_	_	_	_	_	_	_
3	from	_	_	_	_	_	_	_	_
4	Apisal	_	_	_	_	_	_	_	_
5	2.	_	_	_	_	_	_	_	_

# sent_id 6
1	nibru{ki}-sze3	_	_	_	_	_	_	_	_
2	siki	_	_	_	_	_	_	_	_
3	ba-a-si	_	_	_	_	_	_	_	_
4	#tr.en:	_	_	_	_	_	_	_	_
5	to	_	_	_	_	_	_	_	_
6	Nippur,	_	_	_	_	_	_	_	_
7	with	_	_	_	_	_	_	_	_
8	wool	_	_	_	_	_	_	_	_
9	filled,	_	_	_	_	_	_	_	_
10	3.	_	_	_	_	_	_	_	_

# sent_id 7
1	giri3	_	_	_	_	_	_	_	_
2	ur-e11-e	_	_	_	_	_	_	_	_
3	#tr.en:	_	_	_	_	_	_	_	_
4	via	_	_	_	_	_	_	_	_
5	Ur-e’e,	_	_	_	_	_	_	_	_
6	4.	_	_	_	_	_	_	_	_

# sent_id 8
1	mu	_	_	_	_	_	_	_	_
2	ur-bi2-lum{ki}	_	_	_	_	_	_	_	_
3	ba-hul	_	_	_	_	_	_	_	_
4	#tr.en:	_	_	_	_	_	_	_	_
5	year:	_	_	_	_	_	_	_	_
6	“Urbilum	_	_	_	_	_	_	_	_
7	was	_	_	_	_	_	_	_	_
8	destroyed.”	_	_	_	_	_	_	_	_
9	#	_	_	_	_	_	_	_	_
10	Šulgi	_	_	_	_	_	_	_	_
11	45	_	_	_	_	_	_	_	_



&P427604 = CUSAS 06, 224-226
#atf: lang sux
@tablet
@obverse
1. 1(disz) szah2-ze2-da
#tr.en: 1 piglet,
2. iti u4 1(disz) ba-zal
#tr.en: of the month, 1st day passed;
3. 1(disz) udu niga
#tr.en: 1 grain-fed sheep,
4. iti u4 1(u) ba-zal
#tr.en: of the month, 10th day passed;
5. 1(disz) szah2-ze2-da
#tr.en: 1 piglet,
6. iti u4 1(u) 5(disz) ba-zal
#tr.en: of the month, 15th day passed;
7. 1(disz) udu niga
#tr.en: 1 grain-fed sheep,
8. iti u4 2(u) ba-zal
#tr.en: of the month, 20th day passed;
9. 1(disz)# udu# [niga]
#tr.en: 1 [grain-fed] sheep,
10. [iti u4 2(u) 8(disz) ba-zal]
#tr.en: [of the month, 28th day passed];
@reverse
1. sa2-du11 ki-a-nag# [szu-kab-ta2]
#tr.en: rations of the libation place of [Šukabta],
3. ki {d}iszkur-illat-ta
#tr.en: out of Adad-tillati(’s account)
4. ba-zi
#tr.en: booked;
5. sza3 gar-sza-an-na{ki}
#tr.en: in Garšana;
6. iti ezem-{d}nin-a-zu
#tr.en: month: “Festival of Ninazu;”
7. mu {d}szu-{d}suen lugal uri5{ki}-ma-[ke4] e2 {d}szara2 umma{ki}-ka mu-[du3]
#tr.en: year: “Šu-Suen, king of Ur, erected the house of Šara in Umma;”
@left
1. gaba-ri
#tr.en: copy.


&P102359 = ASJ 09, 272 83
#atf: lang sux
@tablet
@obverse
1. 1(u) 1(disz) kusz gu4 niga
#tr.en: 11 ox-hides, grain-fed,
2. 7(gesz2) 3(u) la2 1(disz) kusz udu
#tr.en: 429 sheep-hides,
3. 2(disz) kusz sila4
#tr.en: 2 lamb-hides,
4. sa2-du11 {d}szara2 umma{ki}
#tr.en: regular offerings of Šara of Umma;
5. 1(disz) kusz gu4 niga 2(disz) kusz udu niga
#tr.en: 1 ox-hide, grain-fed, 2 sheep-hides, grain-fed,
6. 3(u) 7(disz) kusz udu
#tr.en: 37 sheep-hides,
7. sa2-du11 {d}szara2 |KI.AN|[{ki}]
#tr.en: regular offerings of Šara of KI.AN;
8. 4(u) 7(disz) kusz udu niga 3(u) kusz sila4
#tr.en: 47 sheep-hides, grain-fed, 30 lamb-hides,
9. nig2-{gesz}tag-ga# [lugal]
#tr.en: royal sacrifice;
10. 1(disz) kusz gu4 niga
#tr.en: 1 ox-hide, grain-fed,
11. 1(gesz2) la2 2(disz) kusz udu niga
#tr.en: 58 sheep-hides, grain-fed,
12. 3(u) 2(disz) kusz udu
#tr.en: 32 sheep-hides,
13. sza3 sa2-du11 [(x)]
#tr.en: in the regular offerings ...;
14. 1(u) 2(disz) kusz masz2
#tr.en: 12 billy goat-hides,
15. sa2-du11 dah-ha {d}szul-gi
#tr.en: regular offerings, additional, of Šulgi;
16. 5(u) kusz udu 2(u) 1(disz) kusz sila4
#tr.en: 50 sheep-hides, 21 lamb-hides,
17. {d}nin-ur4-ra
#tr.en: for Ninura;
18. 1(u) kusz udu 7(disz) kusz sila4
#tr.en: 10 sheep-hides, 7 lamb-hides,
@reverse
1. {d}eb-gal
#tr.en: (for) Ebgal;
2. 1(u) kusz udu 8(disz) kusz sila4
#tr.en: 1 sheep-hide, 8 lamb-hides,
3. {d}en-lil2
#tr.en: (for) Enlil;
4. 1(disz) kusz udu {d}nansze <umma>{ki}
#tr.en: 1 sheep-hides (for) Nanše of Umma;
5. 1(disz) kusz udu {d}gu-la [(x)]
#tr.en: 1 sheep-hide for Gula;
6. 3(u) 1(disz) kusz udu 2(u) kusz [x]
#tr.en: 30 sheep-hides, 20 ...-hides,
7. {d}inanna zabala{ki} [{d}nin]-ildu3#-ma u3 {d}ku3-[sig17-banda3{da}]
#tr.en: for Innana of Zabala, Nin-ilduma and Kusig-banda;
8. 3(disz) kusz udu ensi2 x [...]
#tr.en: 3 sheep-hides, for the governor of ...;
9. 6(disz) kusz udu 4(disz) kusz [...]
#tr.en: 6 sheep-hides, 4 ...-hides,
10. {d}e11-[e?] x [x]
#tr.en: for E’e ...;
11. 4(disz) kusz udu 2(disz) [kusz x]
#tr.en: 4 sheep-hides, 2 ...-hides,
12. {d}da-lagasz#[{ki}]
#tr.en: for Da-Lagaš;
13. 8(disz) kusz udu 4(disz) kusz sila4
#tr.en:8 sheep-hides, 4 lamb-hides,
14. {d}en-ki u3 {d}USZ#-ka-limmu5
#tr.en: for Enki and UŠkalimmu;
15. 4(disz) kusz udu 2(disz) kusz sila4
#tr.en: 4 sheep-hides, 2 lamb-hides,
16. {d}dumu-zi iri-min
#tr.en: for Dumuzi of double-city;
17. sa2-du11 dingir-e-ne
#tr.en: regular offerings of the gods;
18. mu us2-sa bad3 ba-du3
#tr.en: year after: “The wall was erected.”
