# Joint Sentiment/Topic Model for Sentiment Analysis

PDF [https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.163.5917&rep=rep1&type=pdf](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.163.5917&rep=rep1&type=pdf).

Dai dati sono state rimosse le stopwords. Cinque topic per sentiment label, dieci parole per topic.

Script: [https://github.com/linron84/JST](https://github.com/linron84/JST).
Parametri: nsentiLabs=3, ntopics=5, niters=1000, savestep=200, updateParaStep=40, twords=10.

# Risultati

- Sentiment lexicon con solo parole positive e negative, score decimale come da paper.

|  | Topic 0 | Topic 1 | Topic 2 | Topic 3 | Topic 4 |
|---|---|---|---|---|---|
| POS | magnus pater  caesar urbs carmen redeo uis laetus nomen dux | iuuenis rex nouus labor parens mos genus aqua premo quatio | deus domus dies dulcis bonus duco ignis bellum tempus manus | animus paruus munus mens liber uirtus cresco fortis dono tener | gratus uir modus amicus fides diues ago fatum pars neue |
| NEG | grauis equus arma uultus populus miles acer uiuo pereo secundus | quaero mater metuo bene reddo careo ludo rideo proelium aura | mare saeuus durus heu muto sanguis gens nefas celer timeo | pono uentus barbarus beatus credo mitto malus arcus albus cithara | iuppiter longus tollo cura mors impius uoco unda bibo ferox |


- Sentiment lexicon con parole neutre, positive e negative, score intero.

|  | Topic 0 | Topic 1 | Topic 2 | Topic 3 | Topic 4 |
|---|---|---|---|---|---|
| POS | audio nouus modus fides parens amicus ter dono integer aura | uenus dulcis amor teneo merum nobilis flos gaudeo puella pulcher | caesar laetus dux ludo musa fortis clarus ripa aurum phoebus | bonus gratus uir diues redeo beatus uinum lenis premo tutus | animus urbs liber uirtus uis mens mos munus mitto sacer |
| NEG | grauis iuuenis cura saeuus uolo reddo muto fallo peto bacchus | uiuo patior pauper mars superbus coniux hostis iubeo roma propero | labor equus mors impius frons uultus tango ferox pereo puluis | quaero celer timeo nefas proelium credo fugio silua tristis malus | pono metuo durus uentus heu parco humerus arcus occupo crinis |


- Sentiment lexicon con parole neutre, positive e negative, score decimale come da paper.

|  | Topic 0 | Topic 1 | Topic 2 | Topic 3 | Topic 4 |
|---|---|---|---|---|---|
| POS | uenus amor ludo flos amo rosa candidus cadus iubeo maneo | iuppiter quaero urbs munus uirtus dux liber nomen aequor parco | uir animus beatus bene mens uiuo cresco fortis musa clarus | audio modus amicus uis integer pulcher altus fatum breuis soror | dulcis bonus gratus rex nouus fides diues uinum mos merum |
| NEG | grauis mors arma ferox acer pereo leo mars hostis funus | pono equus uentus durus heu timeo moueo nefas gens proelium | labor metuo teneo frons patior honor superus nemus bacchus mons | ago muto careo neue iugum humerus sagitta miser albus uagus | fugio celer parens rapio silua uultus crinis credo aura tristis |