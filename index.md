---
title: ""
keywords: sample homepage
tags: [SRL]
sidebar: mydoc_sidebar
permalink: index.html
summary: This project aims to annotate text in different languages with a layer of "universal" semantic role labeling annotation. For this purpose, we use the frame and role labels of the English Proposition Bank to label shallow semantics in sentences in new target languages.
hide_sidebar: true
---

<!-- {% include warning.html content="This site is under construction." %} -->


**News (2022/04/29)**: Introduced Universal Proposition Bank 2.0 (UP2.0)

**News (2022/01/01)**: UP1.0 Freeze ! 

**News (2019/10/01)**: Two domain-specific Propbank released ([Contract](https://developer.ibm.com/exchanges/data/all/contracts-proposition-bank/), [Finance](https://developer.ibm.com/exchanges/data/all/finance-proposition-bank/))! 

**News (2017/02/10)**: Initial version of Italian UP released!

**News (2017/01/31)**: Initial versions of Finnish, Portuguese and Spanish UP released!


# Release

This is release v2.0 of the Universal Proposition Banks (UP) with significant enhancements over v1.0, including: 
- (1) Propbanks with **higher quality** by using a state-of-the-art monolingual SRL and improved auto-generation of annotations; 
- (2) **Expanded language coverage** (from 7 to 23 [languages](https://universalpropositions.github.io/#languages) ); 
- (3) **Span annotation** for the decoupling of syntactic analysis; and 
- (4) **Gold data** for a subset of the [languages](https://universalpropositions.github.io/#gold-data). 

v2.0 is built upon [release 2.9 of the Universal Dependency Treebanks](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-4611). We use the frame and role labels from the [English Proposition Bank](http://propbank.github.io/) version [3.0](https://github.com/propbank/propbank-documentation/blob/master/other-documentation/Description-of-PB3-changes.md).


## Introduction

This project aims to annotate text in different languages with a layer of "universal" semantic role labeling annotation. For this purpose, we use the frame and role labels of the English Proposition Bank to label shallow semantics in sentences in new target languages. 

For instance, consider the following sentences from different languages: 

<ul id="profileTabs" class="nav nav-tabs"> 
    <li class="active"><a class="noCrossRef" href="#german" data-toggle="tab">German</a></li>
    <li><a class="noCrossRef" href="#french" data-toggle="tab">French</a></li>
    <li><a class="noCrossRef" href="#hindi" data-toggle="tab">Hindi</a></li> 
    <li><a class="noCrossRef" href="#chinese" data-toggle="tab">Chinese</a></li>
</ul>
  <div class="tab-content">
<div role="tabpanel" class="tab-pane active" id="german" markdown="1">

- Sentence: `Ich hatte Gelegenheit eines seiner Seminare zu besuchen.`(_I had the opportunity to attend one of his seminars._). 
- In [CoNLL-U-Plus](https://universaldependencies.org/ext-format.html) format, it looks like this, with English PropBank labels in the last three columns:

|ID | FORM | LEMMA | UPOS | XPOS | FEAT | HEAD | DEPREL | UP:PREDS | UP:ARGHEADS | UP:ARGSPANS|
|-- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --|
|1 | Ich | ich | PRON | PPER | _ | 2 | nsubj | _ | _ | _|
|2 | hatte | haben | VERB | VAFIN | _ | 0 | root | [have.03](https://verbs.colorado.edu/propbank/framesets-english-aliases/have.html) | A0:1\|A1:3 | A0:1-1\|A1:3-3|
|3 | Gelegenheit | Gelegenheit | NOUN | NN | _ | 2 | obj | _ | _ | _|
|4 | eines | ein | DET | PIS | _ | 6 | det | _ | _ | _|
|5 | seiner | sein | DET | PPOSAT | _ | 6 | det:poss | _ | _ | _|
|6 | Seminare | Seminar | NOUN | NN | _ | 8 | obj | _ | _ | _|
|7 | zu | zu | PART | PTKZU | _ | 8 | mark | _ | _ | _|
|8 | besuchen | besuchen | VERB | VVINF | _ | 3 | xcomp | [attend.01](https://verbs.colorado.edu/propbank/framesets-english-aliases/attend.html) | A0:1\|A1:4 | A0:1-1\|A1:4-6|
|9 | . | . | PUNCT | . | _ | 2 | punct | _ | _ | _|

The German verbs
- 'hatte' is labeled as evoking the '**have.03**' frame with two roles: "Ich" (_I_) is labeled **A0** (owner) and "Gelegenheit" (_opportunity_) is labeled **A1** (possession). 
- 'besuchen' is labeled as evoking the '**attend.01**' frame with two roles: "Ich" (_I_) is labeled **A0** (thing attending) and "eines seiner Seminare" (_one of his seminars_) is labeled **A1** (thing attended).
</div>

<div role="tabpanel" class="tab-pane" id="french">
<!--     
- Sentence: `Elle lutte pour échapper aux tueurs à ses trousses.`(_She struggles to escape the killers chasing her._)
- In [CoNLL-U-Plus](https://universaldependencies.org/ext-format.html) format, it looks like this, with English PropBank labels in the last three columns:

|ID | FORM | LEMMA | UPOS | XPOS | FEAT | HEAD | DEPREL | UP:PREDS | UP:ARGHEADS | UP:ARGSPANS|
|-- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --|
|1 | Elle | il | PRON | _ | _ | 2 | nsubj | _ | _ | _|
|2 | lutte | lutter | VERB | _ | _ | 0 | root | [struggle.02](https://verbs.colorado.edu/propbank/framesets-english-aliases/struggle.html) | A0:1\|A1:4 | A0:1-1\|A1:3-10|
|3 | pour | pour | ADP | _ | _ | 4 | mark | _ | _ | _|
|4 | échapper | échapper | VERB | _ | _ | 2 | advcl | [escape.01](https://verbs.colorado.edu/propbank/framesets-english-aliases/escape.html) | A0:1\|A1:7 | A0:1-1\|A1:6-7|
|5-6 | aux | _ | _ | _ | _ | _ | _ | _ | _ | _|
|5 | à | à | ADP | _ | _ | 7 | case | _ | _ | _|
|6 | les | le | DET | _ | _ | 7 | det | _ | _ | _|
|7 | tueurs | tueur | NOUN | _ | _ | 4 | obl:arg | _ | _ | _|
|8 | à | à | ADP | _ | _ | 10 | case | _ | _ | _|
|9 | ses | son | DET | _ | _ | 10 | det | _ | _ | _|
|10 | trousses | trousses | NOUN | _ | _ | 4 | obl:mod | _ | _ | _|
|11 | . | . | PUNCT | _ | _ | 2 | punct | _ | _ | _|

The French verbs
- 'lutte' is labeled as evoking the '**struggle.02**' frame with two roles: "Elle" (_she_) is labeled **A0** (entity trying) and "pour échapper aux tueurs à ses trousses" (_to escape the killers on her trail._) is labeled **A1** (predicative action). 
- 'échapper' is labeled as evoking the '**escape.01**' frame with two roles: "Elle" (_she_) is labeled **A0** (entity escaping) and "les tueurs" (_the killers_) is labeled **A1** (place or thing escaped). -->
<ul>
<li>Sentence: <code>Elle lutte pour échapper aux tueurs à ses trousses.</code>(<em>She struggles to escape the killers chasing her.</em>)</li>
<li>In <a href="https://universaldependencies.org/ext-format.html">CoNLL-U-Plus</a> format, it looks like this, with English PropBank labels in the last three columns:</li>
</ul>
<table>
<thead>
<tr>
<th>ID</th>
<th>FORM</th>
<th>LEMMA</th>
<th>UPOS</th>
<th>XPOS</th>
<th>FEAT</th>
<th>HEAD</th>
<th>DEPREL</th>
<th>UP:PREDS</th>
<th>UP:ARGHEADS</th>
<th>UP:ARGSPANS</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>Elle</td>
<td>il</td>
<td>PRON</td>
<td>_</td>
<td>_</td>
<td>2</td>
<td>nsubj</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>2</td>
<td>lutte</td>
<td>lutter</td>
<td>VERB</td>
<td>_</td>
<td>_</td>
<td>0</td>
<td>root</td>
<td><a href="https://verbs.colorado.edu/propbank/framesets-english-aliases/struggle.html">struggle.02</a></td>
<td>A0:1|A1:4</td>
<td>A0:1-1|A1:3-10</td>
</tr>
<tr>
<td>3</td>
<td>pour</td>
<td>pour</td>
<td>ADP</td>
<td>_</td>
<td>_</td>
<td>4</td>
<td>mark</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>4</td>
<td>échapper</td>
<td>échapper</td>
<td>VERB</td>
<td>_</td>
<td>_</td>
<td>2</td>
<td>advcl</td>
<td><a href="https://verbs.colorado.edu/propbank/framesets-english-aliases/escape.html">escape.01</a></td>
<td>A0:1|A1:7</td>
<td>A0:1-1|A1:6-7</td>
</tr>
<tr>
<td>5-6</td>
<td>aux</td>
<td>_</td>
<td>_</td>
<td>_</td>
<td>_</td>
<td>_</td>
<td>_</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>5</td>
<td>à</td>
<td>à</td>
<td>ADP</td>
<td>_</td>
<td>_</td>
<td>7</td>
<td>case</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>6</td>
<td>les</td>
<td>le</td>
<td>DET</td>
<td>_</td>
<td>_</td>
<td>7</td>
<td>det</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>7</td>
<td>tueurs</td>
<td>tueur</td>
<td>NOUN</td>
<td>_</td>
<td>_</td>
<td>4</td>
<td>obl:arg</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>8</td>
<td>à</td>
<td>à</td>
<td>ADP</td>
<td>_</td>
<td>_</td>
<td>10</td>
<td>case</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>9</td>
<td>ses</td>
<td>son</td>
<td>DET</td>
<td>_</td>
<td>_</td>
<td>10</td>
<td>det</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>10</td>
<td>trousses</td>
<td>trousses</td>
<td>NOUN</td>
<td>_</td>
<td>_</td>
<td>4</td>
<td>obl:mod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>11</td>
<td>.</td>
<td>.</td>
<td>PUNCT</td>
<td>_</td>
<td>_</td>
<td>2</td>
<td>punct</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
</tbody>
</table>
<p>The French verbs</p>
<ul>
<li>&#39;lutte&#39; is labeled as evoking the &#39;<strong>struggle.02</strong>&#39; frame with two roles: &quot;Elle&quot; (<em>she</em>) is labeled <strong>A0</strong> (entity trying) and &quot;pour échapper aux tueurs à ses trousses&quot; (<em>to escape the killers on her trail.</em>) is labeled <strong>A1</strong> (predicative action). </li>
<li>&#39;échapper&#39; is labeled as evoking the &#39;<strong>escape.01</strong>&#39; frame with two roles: &quot;Elle&quot; (<em>she</em>) is labeled <strong>A0</strong> (entity escaping) and &quot;les tueurs&quot; (<em>the killers</em>) is labeled <strong>A1</strong> (place or thing escaped).</li>
</ul>

</div>
    
<div role="tabpanel" class="tab-pane" id="hindi">
<!--     <h2>Hindi</h2> -->
    
<!-- - Sentence: `कुशीनगर की सीमा में प्रवेश करते ही भव्‍य प्रवेशद्वार आपका स्वागत करता है ।`(_The grand entrance welcomes you as you enter the limits of Kushinagar._). 
- In [CoNLL-U-Plus](https://universaldependencies.org/ext-format.html) format, it looks like this, with English PropBank labels in the last three columns:

|ID | FORM | LEMMA | UPOS | XPOS | FEAT | HEAD | DEPREL | UP:PREDS | UP:ARGHEADS | UP:ARGSPANS|
|-- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --|
|1 | कुशीनगर | कुशीनगर | PROPN | NNP | _ | 3 | nmod | _ | _ | _|
|2 | की | का | ADP | PSP | _ | 1 | case | _ | _ | _|
|3 | सीमा | सीमा | NOUN | NN | _ | 6 | obl | _ | _ | _|
|4 | में | में | ADP | PSP | _ | 3 | case | _ | _ | _|
|5 | प्रवेश | प्रवेश | NOUN | NN | _ | 6 | compound | _ | _ | _|
|6 | करते | कर | VERB | VM | _ | 12 | advcl | [enter.01](https://verbs.colorado.edu/propbank/framesets-english-aliases/enter.html) | A1:3 | A1:1-3|
|7 | ही | ही | PART | RP | _ | 6 | dep | _ | _ | _|
|8 | भव्‍य | भव् | ADJ | JJ | _ | 9 | amod | _ | _ | _|
|9 | प्रवेशद्वार | प्रवेशद्वार | NOUN | NN | _ | 12 | nsubj | _ | _ | _|
|10 | आपका | आप | PRON | PRP | _ | 11 | nmod | _ | _ | _|
|11 | स्वागत | स्वागत | NOUN | NN | _ | 12 | compound | _ | _ | _|
|12 | करता | कर | VERB | VM | _ | 0 | root | _ | _ | _|
|13 | है | है | AUX | VAUX | _ | 12 | aux | _ | _ | _|
|14 | \| | \| | PUNCT | SYM | _ | 12 | punct | _ | _ | _|

The Hindi verbs
- 'करते' is labeled as evoking the '**enter.01**' frame with one role: "कुशीनगर की सीमा" (_kushinagar border_) is labeled **A1** (place or thing entered). 
     -->
    
<ul>
<li>Sentence: <code>कुशीनगर की सीमा में प्रवेश करते ही भव्‍य प्रवेशद्वार आपका स्वागत करता है ।</code>(<em>The grand entrance welcomes you as you enter the limits of Kushinagar.</em>). </li>
<li>In <a href="https://universaldependencies.org/ext-format.html">CoNLL-U-Plus</a> format, it looks like this, with English PropBank labels in the last three columns:</li>
</ul>
<table>
<thead>
<tr>
<th>ID</th>
<th>FORM</th>
<th>LEMMA</th>
<th>UPOS</th>
<th>XPOS</th>
<th>FEAT</th>
<th>HEAD</th>
<th>DEPREL</th>
<th>UP:PREDS</th>
<th>UP:ARGHEADS</th>
<th>UP:ARGSPANS</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>कुशीनगर</td>
<td>कुशीनगर</td>
<td>PROPN</td>
<td>NNP</td>
<td>_</td>
<td>3</td>
<td>nmod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>2</td>
<td>की</td>
<td>का</td>
<td>ADP</td>
<td>PSP</td>
<td>_</td>
<td>1</td>
<td>case</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>3</td>
<td>सीमा</td>
<td>सीमा</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>6</td>
<td>obl</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>4</td>
<td>में</td>
<td>में</td>
<td>ADP</td>
<td>PSP</td>
<td>_</td>
<td>3</td>
<td>case</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>5</td>
<td>प्रवेश</td>
<td>प्रवेश</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>6</td>
<td>compound</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>6</td>
<td>करते</td>
<td>कर</td>
<td>VERB</td>
<td>VM</td>
<td>_</td>
<td>12</td>
<td>advcl</td>
<td><a href="https://verbs.colorado.edu/propbank/framesets-english-aliases/enter.html">enter.01</a></td>
<td>A1:3</td>
<td>A1:1-3</td>
</tr>
<tr>
<td>7</td>
<td>ही</td>
<td>ही</td>
<td>PART</td>
<td>RP</td>
<td>_</td>
<td>6</td>
<td>dep</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>8</td>
<td>भव्‍य</td>
<td>भव्</td>
<td>ADJ</td>
<td>JJ</td>
<td>_</td>
<td>9</td>
<td>amod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>9</td>
<td>प्रवेशद्वार</td>
<td>प्रवेशद्वार</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>12</td>
<td>nsubj</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>10</td>
<td>आपका</td>
<td>आप</td>
<td>PRON</td>
<td>PRP</td>
<td>_</td>
<td>11</td>
<td>nmod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>11</td>
<td>स्वागत</td>
<td>स्वागत</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>12</td>
<td>compound</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>12</td>
<td>करता</td>
<td>कर</td>
<td>VERB</td>
<td>VM</td>
<td>_</td>
<td>0</td>
<td>root</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>13</td>
<td>है</td>
<td>है</td>
<td>AUX</td>
<td>VAUX</td>
<td>_</td>
<td>12</td>
<td>aux</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>14</td>
<td>|</td>
<td>|</td>
<td>PUNCT</td>
<td>SYM</td>
<td>_</td>
<td>12</td>
<td>punct</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
</tbody>
</table>
<p>The Hindi verbs</p>
<ul>
<li>&#39;करते&#39; is labeled as evoking the &#39;<strong>enter.01</strong>&#39; frame with one role: &quot;कुशीनगर की सीमा&quot; (<em>kushinagar border</em>) is labeled <strong>A1</strong> (place or thing entered). </li>
</ul>

</div>

<div role="tabpanel" class="tab-pane" id="chinese">
<!--     <h2>Chinese</h2> -->
    
<!-- - Sentence: `他花費了許多時間來比較加拿大地質調查局博物館中的恐龍化石。`(_He spends a lot of time comparing dinosaur fossils in the Geological Survey of Canada museum._). 
- In [CoNLL-U-Plus](https://universaldependencies.org/ext-format.html) format, it looks like this, with English PropBank labels in the last three columns:

|ID | FORM | LEMMA | UPOS | XPOS | FEAT | HEAD | DEPREL | UP:PREDS | UP:ARGHEADS | UP:ARGSPANS|
|-- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --|
|1 | 他 | 他 | PRON | PRP | _ | 7 | nsubj | _ | _ | _|
|2 | 花費 | 花費 | VERB | VV | _ | 7 | advcl | [spend.02](https://verbs.colorado.edu/propbank/framesets-english-aliases/spend.html) | A0:1\|A1:5\|A2:7 | A0:1-1\|A1:4-5\|A2:7-17|
|3 | 了 | 了 | AUX | AS | _ | 2 | aux | _ | _ | _|
|4 | 許多 | 許多 | NUM | CD | _ | 5 | nummod | _ | _ | _|
|5 | 時間 | 時間 | NOUN | NN | _ | 2 | obj | _ | _ | _|
|6 | 來 | 來 | ADV | RB | _ | 7 | mark | _ | _ | _|
|7 | 比較 | 比較 | VERB | VV | _ | 0 | root | [compare.01](https://verbs.colorado.edu/propbank/framesets-english-aliases/compare.html) | A0:1 | A0:1-1|
|8 | 加拿大 | 加拿大 | PROPN | NNP | _ | 13 | nmod | _ | _ | _|
|9 | 地質 | 地質 | NOUN | NN | _ | 13 | nmod | _ | _ | _|
|10 | 調查 | 調查 | VERB | VV | _ | 11 | compound | _ | _ | _|
|11 | 局 | 局 | PART | SFN | _ | 13 | nmod | _ | _ | _|
|12 | 博物 | 博物 | NOUN | NN | _ | 13 | compound | _ | _ | _|
|13 | 館 | 館 | PART | SFN | _ | 17 | nmod | _ | _ | _|
|14 | 中 | 中 | NOUN | NN | _ | 13 | acl | _ | _ | _|
|15 | 的 | 的 | PART | DEC | _ | 13 | case | _ | _ | _|
|16 | 恐龍 | 恐龍 | NOUN | NN | _ | 17 | nmod | _ | _ | _|
|17 | 化石 | 化石 | NOUN | NN | _ | 7 | obj | _ | _ | _|
|18 | 。 | 。 | PUNCT | . | _ | 7 | punct | _ | _ | _|

The Chinese verbs
- '花費' is labeled as evoking the '**spend.02**' frame with roles: "他" (_He_) is labeled **A0** (bider, waiter), "許多時間" (_a lot of time_) is labeled **A1** (unit of time), "比較加拿大地質調查局博物館中的恐龍化石" (_Comparing dinosaur fossils in the Geological Survey of Canada Museum_) is labeled **A2** (activity).
- '比較' is labeled as evoking the '**compare.01**' frame with one role: "他" (_He_) is labeled **A0** ( entity making comparison).
     -->
    
<ul>
<li>Sentence: <code>他花費了許多時間來比較加拿大地質調查局博物館中的恐龍化石。</code>(<em>He spent a lot of time comparing dinosaur fossils in the Geological Survey of Canada museum.</em>). </li>
<li>In <a href="https://universaldependencies.org/ext-format.html">CoNLL-U-Plus</a> format, it looks like this, with English PropBank labels in the last three columns:</li>
</ul>
<table>
<thead>
<tr>
<th>ID</th>
<th>FORM</th>
<th>LEMMA</th>
<th>UPOS</th>
<th>XPOS</th>
<th>FEAT</th>
<th>HEAD</th>
<th>DEPREL</th>
<th>UP:PREDS</th>
<th>UP:ARGHEADS</th>
<th>UP:ARGSPANS</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>他</td>
<td>他</td>
<td>PRON</td>
<td>PRP</td>
<td>_</td>
<td>7</td>
<td>nsubj</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>2</td>
<td>花費</td>
<td>花費</td>
<td>VERB</td>
<td>VV</td>
<td>_</td>
<td>7</td>
<td>advcl</td>
<td><a href="https://verbs.colorado.edu/propbank/framesets-english-aliases/spend.html">spend.02</a></td>
<td>A0:1|A1:5|A2:7</td>
<td>A0:1-1|A1:4-5|A2:7-17</td>
</tr>
<tr>
<td>3</td>
<td>了</td>
<td>了</td>
<td>AUX</td>
<td>AS</td>
<td>_</td>
<td>2</td>
<td>aux</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>4</td>
<td>許多</td>
<td>許多</td>
<td>NUM</td>
<td>CD</td>
<td>_</td>
<td>5</td>
<td>nummod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>5</td>
<td>時間</td>
<td>時間</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>2</td>
<td>obj</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>6</td>
<td>來</td>
<td>來</td>
<td>ADV</td>
<td>RB</td>
<td>_</td>
<td>7</td>
<td>mark</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>7</td>
<td>比較</td>
<td>比較</td>
<td>VERB</td>
<td>VV</td>
<td>_</td>
<td>0</td>
<td>root</td>
<td><a href="https://verbs.colorado.edu/propbank/framesets-english-aliases/compare.html">compare.01</a></td>
<td>A0:1</td>
<td>A0:1-1</td>
</tr>
<tr>
<td>8</td>
<td>加拿大</td>
<td>加拿大</td>
<td>PROPN</td>
<td>NNP</td>
<td>_</td>
<td>13</td>
<td>nmod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>9</td>
<td>地質</td>
<td>地質</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>13</td>
<td>nmod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>10</td>
<td>調查</td>
<td>調查</td>
<td>VERB</td>
<td>VV</td>
<td>_</td>
<td>11</td>
<td>compound</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>11</td>
<td>局</td>
<td>局</td>
<td>PART</td>
<td>SFN</td>
<td>_</td>
<td>13</td>
<td>nmod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>12</td>
<td>博物</td>
<td>博物</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>13</td>
<td>compound</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>13</td>
<td>館</td>
<td>館</td>
<td>PART</td>
<td>SFN</td>
<td>_</td>
<td>17</td>
<td>nmod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>14</td>
<td>中</td>
<td>中</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>13</td>
<td>acl</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>15</td>
<td>的</td>
<td>的</td>
<td>PART</td>
<td>DEC</td>
<td>_</td>
<td>13</td>
<td>case</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>16</td>
<td>恐龍</td>
<td>恐龍</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>17</td>
<td>nmod</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>17</td>
<td>化石</td>
<td>化石</td>
<td>NOUN</td>
<td>NN</td>
<td>_</td>
<td>7</td>
<td>obj</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>18</td>
<td>。</td>
<td>。</td>
<td>PUNCT</td>
<td>.</td>
<td>_</td>
<td>7</td>
<td>punct</td>
<td>_</td>
<td>_</td>
<td>_</td>
</tr>
</tbody>
</table>
<p>The Chinese verbs</p>
<ul>
<li>&#39;花費&#39; is labeled as evoking the &#39;<strong>spend.02</strong>&#39;  frame with roles: &quot;他&quot; (<em>He</em>) is labeled <strong>A0</strong> (bider, waiter), &quot;許多時間&quot; (<em>a lot of time</em>) is labeled <strong>A1</strong> (unit of time), &quot;比較加拿大地質調查局博物館中的恐龍化石&quot; (<em>Comparing dinosaur fossils in the Geological Survey of Canada Museum</em>) is labeled <strong>A2</strong> (activity).</li>
<li>&#39;比較&#39; is labeled as evoking the &#39;<strong>compare.01</strong>&#39; frame with one role: &quot;他&quot; (<em>He</em>) is labeled <strong>A0</strong> ( entity making comparison).</li>
</ul>



</div>
    
</div>

Using this data, we can create SRL systems that predict English PropBank labels for many different languages. See a demo screencast of this SRL for English, French and German [**here**](https://vimeo.com/161718580). 


### Format 
#### Data
The universal propbank (UP) for each language consists of three files (training, dev, and test data) with the extension `.conllup`.

The [conllup](https://universaldependencies.org/ext-format.html) format adds user defined columns to the original 10 columns from the CoNLL-U format (from UD). Our data consists of four columns: the original `ID` columns, plus three additional columns `UP:PRED`, `UP:ARGHEADS`, and `UP:ARGSPANS`.
- **ID** (column 1) is the token id consistent with corresponding UD sentence.
- **UP:PRED** (column 11) contains predicate sense label for this predicate. This sense provides roleset specific meanings for each of its arguments, as defined in EN propbank.
- **UP:ARGHEADS** (column 12) contains the argument heads for arguments of this predicate. Each argument is in the format `label:token_id`.  The arguments are separated by pipe `|` charactor.
- **UP:ARGSPANS** (column 13) contains the argument spans for arguments of this predicate. Each argument is in the format `label:start_token_id-end_token_id`.  The arguments are separated by pipe `|` charactor.

#### Repository
A UP release contains treebanks of the corresponding UD release. Since UP is automatically generated silver data we also release hand annotated EN SRL labels for a subset of the lanaguges to facilitate the research community to perform fair evaluation of their multilingual and cross-lingual SRL systems. To differentiate Gold from UP data we use the following conventions:
- `UP_<language>-<corpus>`
- `GOLD_<language>-<corpus>`

In addition, each language has a folder with verb overview files (produced from the frame files) in HTML format. These files can be viewed in a browser and give an overview of all English frames that each target language verb can evoke.

#### Script
We provide a python script to combine such a UP file with its corresponding UD file to produce the desired 13 column `.conllup` file. The script is available in [tools](https://github.com/UniversalPropositions/tools) repository: `up2/merge_ud_up.py`. 
It takes three arguments:

- `input_ud` - input UD_file or input UD_folder

- `input_up` - input UP_file or input UP_folder

- `output` - output folder for combined output

Below is a sample execution with UD_folder and UP_folder - all the corresponding files from both folders (including subfolders) will be processed during one execution. 
```
python3 up2/merge_ud_up.py input_ud=./tests/data/ud/hi/ --input_up=./tests/data/up/hi/ --output=./tests/data/ud-up/hi/
```
An analogical execution with the specific UD_file and UP_file is presented below:
```
python3 up2/merge_ud_up.py input_ud=./tests/data/ud/hi/hi_hdtb-ud-dev.conllu --input_up=./tests/data/up/hi/hi_hdtb-up-dev.conllu --output=./tests/data/ud-up/hi/hi_hdtb-ud-up-dev.conllu
```


### Scope

Our current focus is to annotate all target language verbs with appropriate English frames. This means that the scope of frame-evoking elements is currently limited to verbs. We also do not label target language auxiliary verbs. For each universal propbank, about 90% of all verbs are currently labeled. Unlabeled verbs often convey semantics for which we either could not find an appropriate English verb, or are part of complex verb constructions which we currently do not handle. 

### A note on quality 

This is an ongoing research project in which we use a combination of data-driven methods and some post-processing to generate these resources. This means that the labels in the UPs are mostly predicted over models trained on a different domain, which affects the quality. A good example is the German verb "angeben" which in our source data was mostly used in the "brag.01" sense, but in the German UD data is mostly used in the "report.01" sense, but almost never detected as such. We provide the languages specific observations in their respective README files. 

## Known Usages 
<!-- ###  -->
- (1) Foundation for Expanded Shallow Semantic Parsing (ESSP), a major differentiating advanced NLP primitive in Watson NLP, an embedding NLP library used widely within IBM products and solutions; 
- (2) Powers multiple IBM products and solutions such as Watson Discovery.

<!-- ### Scientific Impact
- (1) Public dataset; 
- (2) Multiple research papers on data generation, curation, model building at top NLP conferences; 
- (3) More to come in the near future. -->


## Current and future work

This is an ongoing project which we are improving along these lines:
- (1) We are working on adding new languages to the current release.
- (2) We are working to curate the data to improve the quality of SRL annotation.
- (3) We are looking into extending the scope of frame-evoking-elements to other types of predicates besides verbs.
<!-- - (4) We will migrate the data to the newer UD standard.  -->


## Citing UP in papers
If you use UP in your work, please cite these papers:

```
@InProceedings{jindal-etal-2022-UP20,
  author = {Ishan Jindal and Alexandre Rademaker and Michał Ulewicz and Linh Ha and Huyen Nguyen and Khoi-Nguyen Tran and Huaiyu Zhu and Yunyao Li},
  title = "{Universal Proposition Bank 2.0}",
  booktitle = {Proceedings of the Thirteenth International Conference on Language Resources and Evaluation (LREC 2022)},
  year = {2022},
  month = {June 21-23, 2022},
  address = {Marseille, France},
  publisher = {European Language Resources Association (ELRA)},
  isbn = {979-10-95546-72-6},
  language = {english}
  }
```

```
@inproceedings{akbik-etal-2015-generating,
    title = "Generating High Quality Proposition {B}anks for Multilingual Semantic Role Labeling",
    author = "Akbik, Alan  and
      Chiticariu, Laura  and
      Danilevsky, Marina  and
      Li, Yunyao  and
      Vaithyanathan, Shivakumar  and
      Zhu, Huaiyu",
    booktitle = "Proceedings of the 53rd Annual Meeting of the Association for Computational Linguistics and the 7th International Joint Conference on Natural Language Processing (Volume 1: Long Papers)",
    month = jul,
    year = "2015",
    address = "Beijing, China",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/P15-1039",
    doi = "10.3115/v1/P15-1039",
    pages = "397--407",
}
```
## Publications

[Universal Proposition Bank 2.0](). Ishan Jindal, Alexandre Rademaker, Michał Ulewicz, Linh Ha, Huyen Nguyen, Khoi-Nguyen Tran, Huaiyu Zhu and Yunyao Li. *LREC2022.

[Learning Explainable Linguistic Expressions with Neural Inductive Logic Programming for Sentence Classification](https://www.aclweb.org/anthology/2020.emnlp-main.345/). Prithviraj Sen, Marina Danilevsky, Yunyao Li, Siddhartha Brahma, Matthias Boehm, Laura Chiticariu and Rajasekar Krishnamurthy. *2020 Conference on Empirical Methods in Natural Language Processing (EMNLP)* EMNLP 2020.

[A Novel Workflow for Accurately and Efficiently Crowdsourcing Predicate Senses and Argument Labels](https://www.aclweb.org/anthology/2020.findings-emnlp.38/). Youxuan Jiang, Huaiyu Zhu, Jonathan K. Kummerfeld, Yunyao Li and Walter Lasecki. *2020 Conference on Empirical Methods in Natural Language Processing: Findings (EMNLP)* EMNLP: Findings 2020.

[CLAR: A Cross-Lingual Argument Regularizer for Semantic Role Labeling](https://www.aclweb.org/anthology/2020.findings-emnlp.279/). Ishan Jindal, Yunyao Li, Siddhartha Brahma and Huaiyu Zhu. *2020 Conference on Empirical Methods in Natural Language Processing: Findings (EMNLP)* EMNLP: Findings 2020.

[Learning Explainable Linguistic Expressions with Neural Inductive Logic Programming for Sentence Classification](https://www.aclweb.org/anthology/P19-3023/). Prithviraj Sen, Yunyao Li, Eser Kandogan, Yiwei Yang and Walter Lasecki. *2019 57th Annual Meeting of the Association for Computational Linguistics: System Demonstrations* ACL:System Demonstration 2019.

[Crowd-in-the-Loop: A Hybrid Approach for Annotating Semantic Roles](https://www.aclweb.org/anthology/D17-1205). Chenguang Wang, Alan Akbik, Laura Chiticariu, Yunyao Li, Fei Xia and Anbang Xu. *2017 Conference on Empirical Methods on Natural Language Processing* EMNLP 2017.

[Active Learning for Black-Box Semantic Role Labeling with Neural Factors](http://static.ijcai.org/proceedings-2017/0405.pdf). Chenguang Wang, Laura Chiticariu and Yunyao Li. *2017 International Joint Conference on Artificial Intelligence* IJCAI 2017.

[Multilingual Aliasing for Auto-Generating Proposition Banks](http://alanakbik.github.io/papers/COLING_2016_aliasing.pdf). Alan Akbik, Xinyu Guan and Yunyao Li. *26th International Conference on Computational Linguistics* COLING 2016.

[K-SRL: Instance-based Learning for Semantic Role Labeling](http://alanakbik.github.io/papers/K_SRL.pdf). Alan Akbik and Yunyao Li. *26th International Conference on Computational Linguistics* COLING 2016.

[Multilingual Information Extraction with PolyglotIE](http://alanakbik.github.io/papers/coling2016-demo.pdf). Alan Akbik, Laura Chiticariu, Marina Danilevsky, Yonas Kbrom, Yunyao Li and Huaiyu Zhu. *26th International Conference on Computational Linguistics* COLING 2016.

[Towards Semi-Automatic Generation of Proposition Banks for Low-Resource Languages](http://alanakbik.github.io/papers/EMNLP-final.pdf). Alan Akbik, Vishwajeet Kumar and Yunyao Li. *2016 Conference on Empirical Methods on Natural Language Processing* EMNLP 2016.

[Polyglot: Multilingual Semantic Role Labeling with Unified Labels](http://alanakbik.github.io/papers/acl2016-demo.pdf). Alan Akbik and Yunyao Li. *54th Annual Meeting of the Association for Computational Linguistics* ACL 2016.

[Generating High Quality Proposition Banks for Multilingual Semantic Role Labeling](http://alanakbik.github.io/papers/acl2015.pdf). Alan Akbik, Laura Chiticariu, Marina Danilevsky, Yunyao Li, Shivakumar Vaithyanathan and Huaiyu Zhu. *53rd Annual Meeting of the Association for Computational Linguistics* ACL 2015.

### Preprints
[Improved Semantic Role Labeling using Parameterized Neighborhood Memory Adaptation](https://arxiv.org/pdf/2011.14459.pdf). Ishan Jindal, Ranit Aharonov, Siddhartha Brahma, Huaiyu Zhu and Yunyao Li. *arXiv preprint arXiv:2011.14459*


## People

### Contact
For questions, comments, and feedback, click on the `Feedback` link on the top of this page. 

### Core Team

* [Ishan Jindal](https://ijindal.github.io/), IBM Research - Almaden
* [Alexandre Rademaker](http://researcher.ibm.com/researcher/view.php?person=br-alexrad), IBM Research - Brazil
* [Michał Ulewicz](https://michalu.github.io/), Kyndryl, Poland
* [Alan Akbik](http://alanakbik.github.io/), Humboldt-Universität zu Berlin, Germany
* [Laura Chiticariu](http://researcher.watson.ibm.com/researcher/view.php?person=us-chiti), IBM Watson
* [Marina Danilevsky](http://researcher.watson.ibm.com/researcher/view.php?person=us-mdanile), IBM Research - Almaden
* [Huaiyu Zhu](http://researcher.watson.ibm.com/researcher/view.php?person=us-huaiyu), IBM Research - Almaden
* [Khoi-Nguyen Tran](https://kndtran.github.io/), IBM Research - Almaden
* [Yunyao Li](http://yunyaoli.github.io/), Apple 

<!-- ### Contributors

* Xinyu Guan, Yale University
* Tomer Mahlin, IBM Systems Division, Israel
* Vishwajeet Kumar, IIT Bombay
* [Fei Xia](http://faculty.washington.edu/fxia), University of Washington
* Chenguang (Ray) Wang, Amazon
* Linh Ha, Vietnam National University
* Huyen Nguyen, Vietnam National University -->


## Languages

- Currently, UP data is available for 23 languages.

|ID | Language| Corpus| Notes|
|-- | -- | -- | --|
|cs | Czech |[CAC](https://github.com/UniversalPropositions/UP_Czech-CAC), [CLTT](https://github.com/UniversalPropositions/UP_Czech-CLTT), [FicTree](https://github.com/UniversalPropositions/UP_Czech-FicTree), [PDT](https://github.com/UniversalPropositions/UP_Czech-PDT) |  |
|de | German| [GSD](https://github.com/UniversalPropositions/UP_German-GSD), [HDT](https://github.com/UniversalPropositions/UP_German-HDT) |  |
|el | Greek| [GDT](https://github.com/UniversalPropositions/UP_Greek-GDT)|  |
|es | Spanish| [GSD](https://github.com/UniversalPropositions/UP_Spanish-GSD), [AnCora](https://github.com/UniversalPropositions/UP_Spanish-AnCora)  |  |
|fi | Finnish| [TDT](https://github.com/UniversalPropositions/UP_Finnish-TDT), [FTB](https://github.com/UniversalPropositions/UP_Finnish-FTB) |  |
|fr | French| [GSD](https://github.com/UniversalPropositions/UP_French-GSD), [Rhapsodie](https://github.com/UniversalPropositions/UP_French-Rhapsodie), [Sequoia](https://github.com/UniversalPropositions/UP_French-Sequoia) |  |
|hi | Hindi| [HDTB](https://github.com/UniversalPropositions/UP_Hindi-HDTB) |  |
|hu | Hungarian| [Szeged](https://github.com/UniversalPropositions/UP_Hungarian-Szeged) |  |
|id | Indonesian| [GSD](https://github.com/UniversalPropositions/UP_Indonesian-GSD) |  |
|it | Italian| [ISDT](https://github.com/UniversalPropositions/UP_Italian-ISDT), [ParTUT](https://github.com/UniversalPropositions/UP_Italian-ParTUT), [PoSTWITA](https://github.com/UniversalPropositions/UP_Italian-PoSTWITA), [TWITTIRO](https://github.com/UniversalPropositions/UP_Italian-TWITTIRO), [VIT](https://github.com/UniversalPropositions/UP_Italian-VIT) |  |
|ja | Japanese| [GSD](https://github.com/UniversalPropositions/UP_Japanese-GSD) |  |
|ko | Korean| [GSD](https://github.com/UniversalPropositions/UP_Korean-GSD), [Kaist](https://github.com/UniversalPropositions/UP_Korean-Kaist) |  |
|mr | Marathi| [UFAL](https://github.com/UniversalPropositions/UP_Marathi-UFAL) |  |
|nl | Dutch| [Alpino](https://github.com/UniversalPropositions/UP_Dutch-Alpino), [LassySmall](https://github.com/UniversalPropositions/UP_Dutch-LassySmall) |  |
|pl | Polish| [LFG](https://github.com/UniversalPropositions/UP_Polish-LFG), [PDB](https://github.com/UniversalPropositions/UP_Polish-PDB) |  |
|pt | Portuguese| [Bosque](https://github.com/UniversalPropositions/UP_Portuguese-Bosque), [GSD](https://github.com/UniversalPropositions/UP_Portuguese-GSD) |  |
|ro | Romanian| [Nonstandard](https://github.com/UniversalPropositions/UP_Romaniane-Nonstandard), [RRT](https://github.com/UniversalPropositions/UP_Romaniane-RRT), [SiMoNERo](https://github.com/UniversalPropositions/UP_Romaniane-SiMoNERo) |  |
|ru | Russian| [GSD](https://github.com/UniversalPropositions/UP_Russian-GSD), [Taiga](https://github.com/UniversalPropositions/UP_Russian-Taiga), [SynTagRus](https://github.com/UniversalPropositions/UP_Russian-SynTagRus) |  |
|ta | Tamil| [TTB](https://github.com/UniversalPropositions/UP_Tamil-TTB) |  |
|te | Telugu| [MTG](https://github.com/UniversalPropositions/UP_Telugu-MTG) |  |
|uk | Ukrainian| [IU](https://github.com/UniversalPropositions/UP_Ukrainian-IU) |  |
|vi | Vietnamese|[VTB](https://github.com/UniversalPropositions/UP_Vietnamese-VTB) |  |
|zh | Chinese| [GSD](https://github.com/UniversalPropositions/UP_Chinese-GSD) |  |

### Gold Data

- Gold data is  for 3 languages.

|ID | Language| Corpus| Notes|
| -- | -- | -- | -- |
|pt | Portuguese | [Bosque](https://github.com/UniversalPropositions/GOLD_Portuguese-Bosque) |  |
|pl | Polish| [TrOntonotes](https://github.com/UniversalPropositions/GOLD_Polish-TrOntonotes) |  |
|vi | Vietnamese| [Tatoeba](https://github.com/UniversalPropositions/GOLD_Vietnamese-Tatoeba) | Not yet available externally |


