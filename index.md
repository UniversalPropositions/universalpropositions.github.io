---
title: ""
keywords: sample homepage
tags: [SRL]
sidebar: mydoc_sidebar
permalink: index.html
summary: This project aims to annotate text in different languages with a layer of "universal" semantic role labeling annotation. For this purpose, we use the frame and role labels of the English Proposition Bank to label shallow semantics in sentences in new target languages.
hide_sidebar: true
---

{% include warning.html content="This site is under construction." %}

# Release

This is release 2.0 of the Universal Proposition Banks (UP). It is built upon [release 2.9 of the Universal Dependency Treebanks](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-4611) and inherits their [licence](https://lindat.mff.cuni.cz/repository/xmlui/page/licence-UD-2.9). We use the frame and role labels from the [English Proposition Bank](http://propbank.github.io/) version [3.0](https://github.com/propbank/propbank-documentation/blob/master/other-documentation/Description-of-PB3-changes.md).


**News (2022/01/01)**: UP1.0 Freeze ! 

**News (2019/10/01)**: Two domain-specific Propbank released ([Contract](https://developer.ibm.com/exchanges/data/all/contracts-proposition-bank/), [Finance](https://developer.ibm.com/exchanges/data/all/finance-proposition-bank/))! 

**News (2017/02/10)**: Initial version of Italian UP released!

**News (2017/01/31)**: Initial versions of Finnish, Portuguese and Spanish UP released!


## Multilingual SRL 

Using this data, we can create SRL systems that predict English PropBank labels for many different languages. See a recent demo screencast of this SRL for English, French and German [**here**](https://vimeo.com/161718580). 


## Introduction

This project aims to annotate text in different languages with a layer of "universal" semantic role labeling annotation. For this purpose, we use the frame and role labels of the English Proposition Bank to label shallow semantics in sentences in new target languages. 

For instance, consider the following sentences from different langauges: 

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
- 'besuchen' is labeld as evoking the '**attend.01**' frame with two roles: "Ich" (_I_) is labeled **A0** (thing attending) and "eines seiner Seminare" (_one of his seminars_) is labeled **A1** (thing attended).
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
- 'échapper' is labeld as evoking the '**escape.01**' frame with two roles: "Elle" (_she_) is labeled **A0** (entity escaping) and "les tueurs" (_the killers_) is labeled **A1** (place or thing escaped). -->
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
<li>&#39;lutte&#39; is labeled as evoking the &#39;<strong>struggle.02</strong>&#39; frame with two roles: &quot;Elle&quot; (<em>she</em>) is labeled <strong>A0</strong> (entity trying) and &quot;pour échapper aux tueurs à ses trousses&quot; (<em>to escape the killers on his trail.</em>) is labeled <strong>A1</strong> (predicative action). </li>
<li>&#39;besuchen&#39; is labeld as evoking the &#39;<strong>escape.01</strong>&#39; frame with two roles: &quot;Elle&quot; (<em>she</em>) is labeled <strong>A0</strong> (entity escaping) and &quot;les tueurs&quot; (<em>the killers</em>) is labeled <strong>A1</strong> (place or thing escaped).</li>
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
<li>&#39;花費&#39; is labeled as evoking the &#39;<strong>spend.02</strong>&#39; frame with one role: &quot;他&quot; (<em>He</em>) is labeled <strong>A0</strong> (bider, waiter), &quot;許多時間&quot; (<em>a lot of time</em>) is labeled <strong>A1</strong> (unit of time), &quot;比較加拿大地質調查局博物館中的恐龍化石&quot; (<em>Comparing dinosaur fossils in the Geological Survey of Canada Museum</em>) is labeled <strong>A2</strong> (activity).</li>
<li>&#39;比較&#39; is labeled as evoking the &#39;<strong>compare.01</strong>&#39; frame with one role: &quot;他&quot; (<em>He</em>) is labeled <strong>A0</strong> ( entity making comparison).</li>
</ul>



</div>
    
</div>



### Format 
#### Data
The universal propbank (UP) for each language consists of three files (training, dev and test data) with the extension `.conllup`.

<!-- but currently encoding an extension of the [CoNLL-U format](http://universaldependencies.org/format.html). The extension is based on the CoNLL format produced by the [Propbank conversion scripts](https://github.com/propbank/propbank-release/blob/master/docs/conll-conversion-notes.md), called `.gold_conll`.  -->

The `conllup` formats (Link to definition) adds user defined columns to the original 10 columns from the CoNLL-U format (can be obtained from UD). Our data consists of four columns: the original `ID` columns, plus three additional columns `UP:PRED`, `UP:ARGHEADS`, and `UP:ARGSPANS`.
- **ID** (column 1) is the token id consistent with corresponding UD sentence.
- **UP:PRED** (column 11) contains predicate sense label for this predicate. This sense provides roleset specific meanings for each of its arguments, as defined in EN propbank.
- **UP:ARGHEADS** (column 12) contains the argument heads for arguments of this predicate. Each argument is in the format `label:token_id`.  The arguments are separated by pipe `|` charactor.
- **UP:ARGSPANS** (column 13) contains the argument spans for arguments of this predicate. Each argument is in the format `label:start_token_id-end_token_id`.  The arguments are separated by pipe `|` charactor.

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
<!-- - Every column after the eleventh is a predicate, in order that they appear in the sentence. Note that the Propbank `.gold_conll` files contain a "frame file" column (column 11) that lets you know which ".xml" [file](https://github.com/propbank/propbank-frames/) contains the actual semantic form for the predicate in question (which is not always the same as the predicate: one must reference "lighten.xml" for lighten_up.02), but since all predicate identifier is unique, we haven't preserved this column. -->

#### Repository
A UP release contains treebanks of the corresponding UD release. Since UP is automatically generated silver data we also release hand annotated EN srl labels for a subset of the lanaguges to facilitate the research community to perform fair evaluation of their multilingual and cross-lingual SRL systems. To differentiate Gold from UP data we use the following conventions:
- `UP_<langauge>-<corpus>`
- `GOLD__<langauge>-<corpus>`

In addition, each language has a folder with verb overview files (produced from the frame files) in html format. These files can be viewed in a browser and give an overview of all English frames that each target language verb can evoke.

### Scope

Our current focus is to annotate all target language verbs with appropriate English frames. This means that the scope of frame-evoking elements is currently limited to verbs. We also do not label target language auxiliary verbs. For each universal propbank, about 90% of all verbs are currently labeled. Unlabeled verbs often convey semantics for which we either could not find an appropriate English verb, or are part of complex verb constructions which we currently do not handle. 

### A note on quality 

This is an ongoing research project in which we use a combination of data-driven methods and some post-processing to generate these resources. This means that the labels in the UPs are mostly predicted over models trained on a different domain, which affects the quality. A good example is the German verb "angeben" which in our source data was mostly used in the "brag.01" sense, but in the German UD data is mostly used in the "report.01" sense, but almost never detected as such. We provide the langauges specific observation in their respective README files. 

## Impact 
### Business Impact
- (1) Foundation for Expanded Shallow Semantic Parsing (ESSP), a major differientiating advanced NLP primitive in Watson NLP, an embedding NLP library used widely within IBM products and solutions; 
- (2) Powers multiple IBM products and solutions such as Watson Discovery and AIOps.

### Scientific Impact
- (1) Public dataset; 
- (2) Multiple research papers on data generation, curation, model building at top NLP conferences; 
- (3) More to come in the near future.


## Current and future work

This is an ongoing project which we are improving along three lines: (1) We are working on adding new languages to the current release. (2) We are working to curate the data to improve the quality of SRL annotation. (3) We are looking into extending the scope of frame-evoking-elements to other types of predicates besides verbs. (4) We will migrate the data to newer UD standard. 

## Publications

### Citing UP in papers
If you use UP in your work, please cite these papers:

[Universal Proposition Bank 2.0](). Ishan Jindal, Alexandre Rademaker, Michał Ulewicz, NGUYEN Thi Minh Huyen, HA My Linh, Khoi-Nguyen Tran, Huaiyu Zhu and Yunyao Li. *LREC2022.

[Generating High Quality Proposition Banks for Multilingual Semantic Role Labeling](http://alanakbik.github.io/papers/acl2015.pdf). Alan Akbik, Laura Chiticariu, Marina Danilevsky, Yunyao Li, Shivakumar Vaithyanathan and Huaiyu Zhu. *53rd Annual Meeting of the Association for Computational Linguistics* ACL 2015.

### Other Publications

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
* [Yunyao Li](http://yunyaoli.github.io/), Apple Inc. 

<!-- ### Contributors

* Xinyu Guan, Yale University
* Tomer Mahlin, IBM Systems Division, Israel
* Vishwajeet Kumar, IIT Bombay
* [Fei Xia](http://faculty.washington.edu/fxia), University of Washington
* Chenguang (Ray) Wang, Amazon
* Linh Ha, Vietnam National University
* Huyen Nguyen, Vietnam National University

 -->




<!-- {% include note.html content="If you're cloning this theme, you're probably writing documentation of some kind. I have a blog on technical writing here called <a alt='technical writing blog' href='http://idratherbewriting.com'>I'd Rather Be Writing</a>. If you'd like to stay updated with the latest trends, best practices, and other methods for writing documentation, consider <a href='https://tinyletter.com/tomjoht'>subscribing</a>. I also have a site on <a href='http://idratherbewriting.com/learnapidoc'>writing API documentation</a>." %}

## Build the Theme

Follow these instructions to build the theme.

### 1. Download the theme

First, download or clone the theme from the [Github repo](https://github.com/tomjoht/documentation-theme-jekyll). Most likely you won't be pulling in updates once you start customizing the theme, so downloading the theme (instead of cloning it) probably makes the most sense. In Github, click the **Clone or download** button, and then click **Download ZIP**.

### 2. Install Jekyll

If you've never installed or run a Jekyll site locally on your computer, follow these instructions to install Jekyll:

* [Install Jekyll on Mac][mydoc_install_jekyll_on_mac]
* [Install Jekyll on Windows][mydoc_install_jekyll_on_windows]

### 3. Install Bundler

In case you haven't installed Bundler, install it:

```
gem install bundler
```

You'll want [Bundler](http://bundler.io/) to make sure all the Ruby gems needed work well with your project. Bundler sorts out dependencies and installs missing gems or matches up gems with the right versions based on gem dependencies.

### 4. Option 1: Build the Theme (*without* the github-pages gem) {#option1}

Use this option if you're not planning to publish your Jekyll site using [Github Pages](https://pages.github.com/).

Bundler's Gemfile specifies how project dependencies are managed. Although this project includes a Gemfile, this theme doesn't have any dependencies beyond core Jekyll. The Gemfile is used to list gems needed for publishing on Github Pages. **If you're not planning to have Github Pages build your Jekyll project, delete these two files from the theme's root directory:**

* Gemfile
* Gemfile.lock

If you've never run Jekyll on your computer (you can check with `jekyll --version`), you may need to install the jekyll gem:

```
gem install jekyll
```

Now run jekyll serve (first change directories (`cd`) to where you downloaded the project):

```
jekyll serve
```

### 4. Option 2: Build the Theme (*with* the github-pages gem) {#option2}

If you *are* in fact publishing on Github Pages, leave the Gemfile and Gemfile.lock files in the theme.The Gemfile tells Jekyll to use the github-pages gem. **However, note that you cannot use the normal `jekyll serve` command with this gem due to dependency conflicts between the latest version of Jekyll and Github Pages** (which are noted [briefly here](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)).

You need Bundler to resolve these dependency conflicts. Use Bundler to install all the needed Ruby gems:

```
bundle update
```

Then *always* use this command to build Jekyll:

```
bundle exec jekyll serve
```

If you want to shorten this long command, you can put this code in a file such as jekyll.sh (on a Mac) and then simply type `. jekyll.sh` to build Jekyll.

## Running the site in Docker

You can also use Docker to directly build and run the site on your local machine. Just clone the repo and run the following from your working dir:
```
docker-compose build --no-cache && docker-compose up
```
The site should now be running at [http://localhost:4000/](http://localhost:4000/).

This is perhaps the easiest way to see how your site would actually look.

## Configure the sidebar

There are several products in this theme. Each product uses a different sidebar. This is the essence of what makes this theme unique -- different sidebars for different product documentation. The idea is that when users are reading documentation for a specific product, the sidebar navigation should be specific to that product. (You can read more of my thoughts on why multiple sidebars are important in this [blog post](http://idratherbewriting.com/2016/03/23/release-of-documentation-theme-for-jekyll-50/).)

The top navigation usually remains the same, because it allows users to navigate across products. But the sidebar navigation adapts to the product.

In each page's frontmatter, you must specify the sidebar you want that page to use. Here's an example of the page frontmatter showing the sidebar property:

<pre>
---
title: Alerts
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: "You can insert notes, tips, warnings, and important alerts in your content. These notes are stored as shortcodes made available through the linksrefs.hmtl include."
<span class="red">sidebar: mydoc_sidebar</span>
permalink: mydoc_alerts
---
</pre>

The `sidebar: mydoc_sidebar` refers to the \_data/sidebars/mydoc_sidebar.yml file.

Note that your sidebar can only have 2 levels (expand the **Tag archives** option to see an example of the second level). Given that each product has its own sidebar, this depth should be sufficient (it's really like 3 levels). Deeper nesting goes against usability recommendations.

You can optionally turn off the sidebar on any page (e.g. landing pages). To turn off the sidebar for a page, you should set the page frontmatter tag as `hide_sidebar: true`.

If you don't declare a sidebar, the `home_sidebar` file gets used as the default because this is the default specified in the config file:

```yaml
-
  scope:
    path: ""
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: home_sidebar
    topnav: topnav
```

If you want to set different sidebar defaults based on different folders for your pages, specify your defaults like this:

```
-
  scope:
    path: "pages/mydoc"
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: mydoc_sidebar
    topnav: topnav
```

This would load the `mydoc_sidebar` for each file in **pages/mydoc**. You could set different defaults for different path scopes.

For more detail on the sidebar, see [Sidebar navigation][mydoc_sidebar_navigation].

## Top navigation

The top navigation works just like the sidebar. You can specify which topnav data file should load by adding a `topnav` property in your page, like this:

```yaml
topnav: topnav
```

Here the topnav refers to the `_data/topnav.yml` file.

Because most topnav options will be the same, the `_config.yml` file specifies the topnav file as a default:

```yaml
-
  scope:
    path: ""
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: home_sidebar
    topnav: topnav
```

## Sidebar syntax

The sidebar data file uses a specific YAML syntax that you must follow. Follow the sample pattern shown in the theme, specically looking at `mydoc_sidebar.yml` as an example: Here's a code sample showing all levels:

```yaml
entries:
- title: sidebar
  product: Jekyll Doc Theme
  version: 6.0
  folders:
  - title: Overview
    output: web, pdf
    folderitems:

    - title: Get started
      url: /index.html
      output: web, pdf
      type: homepage

    - title: Introduction
      url: /mydoc_introduction.html
      output: web, pdf

  - title: Release Notes
    output: web, pdf
    folderitems:

    - title: 6.0 Release notes
      url: /mydoc_release_notes_60.html
      output: web, pdf

    - title: 5.0 Release notes
      url: /mydoc_release_notes_50.html
      output: web, pdf

  - title: Tag archives
    output: web
    folderitems:

    - title: Tag archives overview
      url: /mydoc_tag_archives_overview.html
      output: web

      subfolders:
      - title: Tag archive pages
        output: web
        subfolderitems:

        - title: Formatting pages
          url: /tag_formatting.html
          output: web

        - title: Navigation pages
          url: /tag_navigation.html
          output: web

        - title: Content types pages
          url: /tag_content_types.html
          output: web
```

Each `folder` or `subfolder` must contain a `title` and `output` property. Each `folderitem` or `subfolderitem` must contain a `title`, `url`, and `output` property.

The two outputs available are `web` and `pdf`. (Even if you aren't publishing PDF, you still need to specify `output: web`).

The YAML syntax depends on exact spacing, so make sure you follow the pattern shown in the sample sidebars. See my [YAML tutorial](mydoc_yaml_tutorial) for more details about how YAML works.

{% include note.html content="If you have just one character of spacing off, Jekyll won't build due to the YAML syntax error. You'll see an error message in your console that says \"Error ... did not find expected key while parsing a block mapping at line 22 column 5. Error: Run jekyll build --trace for more information.\" If you encounter this, it usually refers to incorrect indentation or spacing in the YAML file. See the example mydoc_sidebar.yml file to see where your formatting went wrong." %}

Each level must have at least one topic before the next level starts. You can't have a second level that contains multiple third levels without having at least one standalone topic in the second level. If you need a hierarchy that has a folder that contains other folders and no loose topics, use a blank `-` item like this:

```yaml
entries:
- title: sidebar
  product: Jekyll Doc Theme
  version: 6.0
  folders:
  - title: Overview
    output: web, pdf
    folderitems:

    -

  - title: Release Notes
    output: web, pdf
    folderitems:

    - title: 6.0 Release notes
      url: /mydoc_release_notes_60.html
      output: web, pdf

    - title: 5.0 Release notes
      url: /mydoc_release_notes_50.html
      output: web, pdf

  - title: Installation
    output: web, pdf
    folderitems:

    - title: About Ruby, Gems, Bundler, etc.
      url: /mydoc_about_ruby_gems_etc.html
      output: web, pdf

    - title: Install Jekyll on Mac
      url: /mydoc_install_jekyll_on_mac.html
      output: web, pdf

    - title: Install Jekyll on Windows
      url: /mydoc_install_jekyll_on_windows.html
      output: web, pdf
```

To accommodate the title page and table of contents in PDF outputs, each product sidebar must list these pages before any other:

```yaml
- title:
  output: pdf
  type: frontmatter
  folderitems:
  - title:
    url: /titlepage
    output: pdf
    type: frontmatter
  - title:
    url: /tocpage
    output: pdf
    type: frontmatter
```

Leave the output as `output: pdf` for these frontmatter pages so that they don't appear in the web output.

For more detail on the sidebar, see [Sidebar navigation][mydoc_sidebar_navigation] and [YAML tutorial][mydoc_yaml_tutorial].

## Comments

The theme integrates [Commento.io](https://commento.io/) for comments below pages and posts. (This commenting service doesn't inject controversial tracking ads like Disqus does.) You will need to Commento.io account + plan ($5/month) to authorize Commento with your domain (no other configuration should be required). If you don't want comments, in the \_config.yml file, change the `comments: true` properties (under `defaults`) to `comments: false` in every instance. Then in the commento.html include file (inside \_includes), the `{% raw %}{% unless page.comments == false %} ... {% endunless %}{% endraw %}` logic will not insert the Commentio form.

## Relative links and offline viewing

This theme uses relative links throughout so that you can view the site offline and not worry about which server or directory you're hosting it. It's common with tech docs to push content to an internal server for review prior to pushing the content to an external server for publication. Because of the need for seamless transferrence from one host to another, the site has to use relative links.

To view pages locally on your machine (without the Jekyll preview server), they need to have the `.html` extension. The `permalink` property in the page's frontmatter (without surrounding slashes) is what pushes the files into the root directory when the site builds.

## Page frontmatter

When you write pages, include these same frontmatter properties with each page:

```yaml
---
title: "Some title"
tags: [sample1, sample2]
keywords: keyword1, keyword2, keyword3
last_updated: Month day, year
summary: "optional summary here"
sidebar: sidebarname
permalink: filename.html
---
```

(You will customize the values for each of these properties, of course.)

For titles, surrounding the title in quotes is optional, but if you have a colon in the title, you must surround the title with quotation marks. If you have a quotation mark inside the title, escape it first with a backlash `\`.

Values for `keywords` get populated into the metadata of the page for SEO.

Values for `tags` must be defined in your \_data/tags.yml list. You also need a corresponding tag file inside the tags folder pages/tags/ that follows the same pattern as the other tag files shown in the tags folder. (Jekyll won't auto-create these tag files.)

If you don't want the mini-TOC to show on a page (such as for the homepage or landing pages), add `toc: false` in the frontmatter.

The `permalink` value should be the same as your filename and include the ".html" file extension.

For more detail, see [Pages][mydoc_pages].

## Where to store your documentation topics

You can store your files for each product inside subfolders following the pattern shown in the theme. For example, product1, product2, etc, can be stored in their own subfolders inside the \_pages directory. Inside \_pages, you can store your topics inside sub-subfolders or sub-sub-folders to your heart's content. When Jekyll builds your site, it will pull the topics into the root directory and use the permalink for the URL.

Note that product1, product2, and mydoc are all just sample content to demonstrate how to add multiple products into the theme. You can freely delete that content.

For more information, see [Pages][mydoc_pages] and [Posts][mydoc_posts].

## Configure the top navigation

The top navigation bar's menu items are set through the \_data/topnav.yml file. Use the top navigation bar to provide links for navigating from one product to another, or to navigate to external resources.

For external URLs, use `external_url` in the item property, as shown in the example topnav.yml file. For internal links, use `url` the same was you do in the sidebar data files.

Note that the topnav has two sections: `topnav` and `topnav_dropdowns`. The topnav section contains single links, while the `topnav_dropdowns` section contains dropdown menus. The two sections are independent of each other.

## Generating PDF

If you want to generate PDF, you'll need a license for [Prince XML](http://www.princexml.com/). You will also need to [install Prince](http://www.princexml.com/doc/installing/).  You can generate PDFs by product (but not for every product on the site combined together into one massive PDF). Prince will work even without a license, but it will imprint a small Prince image on the first page, and you're supposed to buy the license to use it.

If you're on Windows, install [Git Bash client](https://git-for-windows.github.io/) rather than using the default Windows command prompt.

Open up the css/printstyles.css file and customize the email address (`youremail@domain.com`) that is listed there. This email address appears in the bottom left footer of the PDF output. You'll also need to create a PDF configuration file following the examples shown in the pdfconfigs folder, and also customize some build scripts following the same pattern shown in the root: pdf-product1.sh

See the section on [Generating PDFs][mydoc_generating_pdfs] for more details about setting the theme up for this output.

## Blogs / News

For blog posts, create your markdown files in the \_posts folder following the sample formats. Post file names always begin with the date (YYYY-MM-DD-title).

The news/news.html file displays the posts, and the news_archive.html file shows a yearly history of posts. In documentation, you might use the news to highlight product features outside of your documentation, or to provide release notes and other updates.

See [Posts][mydoc_posts] for more information.

## Markdown

This theme uses [kramdown markdown](http://kramdown.gettalong.org/). kramdown is similar to Github-flavored Markdown, except that when you have text that intercepts list items, the spacing of the intercepting text must align with the spacing of the first character after the space of a numbered list item. Basically, with your list item numbering, use two spaces after the dot in the number, like this:

```
1.  First item
2.  Second item
3.  Third item
```

When you want to insert paragraphs, notes, code snippets, or other matter in between the list items, use four spaces to indent. The four spaces will line up with the first letter of the list item (the <b>F</b>irst or <b>S</b>econd or <b>T</b>hird).

```
1.  First item

    ```
    alert("hello");
    ```

2.  Second item

    Some pig!

3.  Third item
```

See the topics under "Formatting" in the sidebar for more information.

## Automated links

If you want to use an automated system for managing links, see [Automated Links][mydoc_hyperlinks.html#automatedlinks]. This approach automatically creates a list of Markdown references to simplify linking.

## Other instructions

The content here is just a getting started guide only. For other details in working with the theme, see the various sections in the sidebar.

{% include links.html %}
 -->
