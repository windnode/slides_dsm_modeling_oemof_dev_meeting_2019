---
author:
- Guido Pleßmann
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

# DSM formualtion 1: Zerrahn \& Schill (interval)

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

# Basic testing data

![](img/DSM-shift-input-data_basic.png)

# How it works

:::::: {.columns}
::: {.column  width=45%} 
![](img/DSM-shift_basic.png)
:::

::: {.column  width=40%}
**Delay time:** ??

\vspace{10pt}

**What's happening**
:::
:::::: 


# Shifting energy exceeding the delay time (basic)

:::::: {.columns}
::: {.column  width=45%} 
![](img/DSM-shift-exceeding-delay-time_basic.png)
:::

::: {.column  width=40%}
**Delay time:** ??

\vspace{10pt}

**What's happening**
:::
:::::: 


# Limited by DSM events in between (50 %)


:::::: {.columns}
::: {.column  width=45%} 
![](img/DSM-shift-exceeding-delay-time_25percent.png)
:::

::: {.column  width=40%}
**Delay time:** ??

\vspace{10pt}

**Intermediate DSM trigger:**\
50 % of $DSM_{up}$

\vspace{10pt}

**What's happening**
:::
:::::: 

# Effect of delay time


:::::: {.columns}
::: {.column  width=45%} 
![](img/DSM-shift-exceeding-delay-time_delay-1.png)
:::

::: {.column  width=40%}
**Delay time:** 1


\vspace{10pt}

**What's happening**
:::
::::::

# Effect of delay time


:::::: {.columns}
::: {.column  width=45%} 
![](img/DSM-shift-exceeding-delay-time_delay-2.png)
:::

::: {.column  width=40%}
**Delay time:** 2


\vspace{10pt}

**What's happening**
:::
::::::

# Effect of delay time

:::::: {.columns}
::: {.column  width=45%} 
![](img/DSM-shift-exceeding-delay-time_delay-3.png)
:::

::: {.column  width=40%}
**Delay time:** 3


\vspace{10pt}

**What's happening**
:::
::::::

# Effect of delay time

:::::: {.columns}
::: {.column  width=45%} 
![](img/DSM-shift-exceeding-delay-time_delay-6.png)
:::

::: {.column  width=40%}
**Delay time:** 6


\vspace{10pt}

**What's happening**
:::
::::::


# Comparing both formulations -- delay method


![](img/DSM-activity_delay-method_4days.png)


