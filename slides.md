---
author:
- Guido Pleßmann\
- Julian Endres
title: DSM modeling in oemof.solph
subtitle: Introducing the custom component SinkDSM
institute: Reiner Lemoine Institut
classoption: aspectratio=169
date: December 4, 2019
theme: rli
...

# Project context

* Research project WindNODE
* Building a regional ESM for Anhalt-Bitterfeld-Wittenberg
* Intended analysis: potential of flexibility options to foster regional energy supply
* Demand-Side Management in households is one option

# DSM modeling for households

Available data: technical DSM potential for groups of households

![](img/IOEW_DSM_Daten_Zusammensetzung.pdf){ width=85% }

<!-- Two DSM model formulations are provided by [SinkDSM](https://oemof.readthedocs.io/en/latest/api/oemof.solph.html#oemof.solph.custom.SinkDSM) -->

# DSM potential

![](img/IOEW_DSM_Daten_Potenzial.pdf){ width=85% }

# DSM formualtion 1: Zerrahn \& Schill

$$\quad \dot{E}_{t} \quad = \quad demand_{t} \quad + \quad DSM_{t}^{up} \quad - \quad \sum_{tt=t-L}^{t+L} DSM_{t,tt}^{do}  \qquad \forall t$$

$$ \quad DSM_{t}^{up} \quad = \quad \sum_{tt=t-L}^{t+L} DSM_{t,tt}^{do} \qquad \forall t $$

$$ \quad DSM_{t}^{up} \quad \leq \quad E_{t}^{up} \qquad \forall t $$

$$ \quad \sum_{t=tt-L}^{tt+L} DSM_{t,tt}^{do} \quad \leq \quad E_{t}^{do} \qquad \forall tt $$

$$ \quad DSM_{tt}^{up} \quad + \quad \sum_{t=tt-L}^{tt+L} DSM_{t,tt}^{do} \quad \leq \quad max \{ E_{t}^{up}, E_{t}^{do} \} \qquad \forall tt $$ 



# DSM formulation 2: Interval

The dataset for DSM potential does not allow to shift energy across days!

$$\quad  E_{t}^{do} < DSM_{t}^{updown} < E_{t}^{up} \quad \forall t$$

$$ \quad \dot{E}_{t} = demand_{t} + DSM_{t}^{updown} \quad \forall t $$

$$ \quad  \sum_{t=0}^{24} DSM_{t}^{updown} = 0 \quad \forall t $$

# How it works

TODO: basic example (graphic) showing intended functionality


# Shifting energy exceeding the delay time

TODO: basic example 

# Shifting energy exceeding the delay time

TODO: describe what's happening

# Limited by DSM events in between

TODO: (maybe multiple slides) Show how the DSM shift that exceeds delay time is limited by other DSM events in between

# Comparing both formulations

TODO: a figure showing how DSM is used in each approach
