# internet-use
The aim of this project is to study the relationship of various factors with the use of the Internet in the Czech Republic. 

**Please scroll down for the English version**

# Факторы, связанные с использованием интернета в Чехии

Анализ данных **European Social Survey, раунд 10** (ESS10, edition 3.3) по **Чехии**.

**Цель проекта:** понять, какие социальные характеристики и ценностные ориентации связаны с тем, сколько времени человек проводит в интернете в обычный день.

Анализ выполнен в ноутбуке [`internet_use_czechia.ipynb`](internet_use_czechia.ipynb).

## Данные

- **Источник:** European Social Survey European Research Infrastructure (ESS ERIC). (2025). *ESS10 — Integrated file, edition 3.3*. Sikt. [https://doi.org/10.21338/ESS10E03_3](https://doi.org/10.21338/ESS10E03_3)
- **Выборка:** респонденты Чехии (`cntry == CZ`), после очистки пропусков - **1 490** наблюдений
- **Зависимая переменная:** `netustm` - время в интернете в обычный день, в минутах
- **Предикторы:** пол, возраст, счастье, социальная активность относительно сверстников, социальное доверие и четыре фактора человеческих ценностей

## Ход анализа

1. **Разведочный анализ.** Отбор переменных, приведение типов, обработка кодов пропусков по кодбуку, построение индекса *social trust* как среднего по `ppltrst`, `pplfair` и `pplhlp`.
2. **Эксплораторный факторный анализ** 21 пункта шкалы человеческих ценностей. Проверены предпосылки (KMO, тест Бартлетта, линейность, выбросы). Из-за нарушения многомерной нормальности использован *Principal Axis Factoring* и ортогональное вращение **Varimax**. По критерию Кайзера выделены **4 фактора** (около **58,8%** общей дисперсии):
   - *Self-Expression & Care for Others*
   - *Hedonism & Achievement*
   - *Conservatism*
   - *Social Conformity*
3. **Линейная регрессия.** Зависимая переменная логарифмирована (`log1p`), стандартные ошибки — робастные (**HC3**). Скорректированный **R² = 0,136**; модель значима.

## Основные результаты

- Чем **выше возраст**, самовыражение, гедонизм и социальное доверие, тем **меньше** времени в интернете.
- Чем **выше консерватизм** и уровень счастья, тем **больше** времени в интернете.
- При **средней** социальной активности интернет используется меньше, чем при очень низкой или очень высокой активности относительно сверстников.
- **Пол** и **социальный конформизм** с использованием интернета **не связаны**.

Ориентиры по величине связей (при прочих равных, на логарифмированной шкале): каждый дополнительный год возраста связан со снижением времени в интернете примерно на **1,1%**; рост консерватизма на 1 стандартное отклонение - с увеличением примерно на **12,4%**; рост гедонизма - со снижением примерно на **8,9%**.

## Содержимое репозитория

| Файл | Описание |
| --- | --- |
| `digital_social_contacts.ipynb` | основной анализ |
| `factor_loadings_varimax.csv` | факторные нагрузки |
| `communalities.csv` | общности |
| `factor_scores.csv` | факторные оценки |

## Основные использованные библиотеки

`pandas`, `numpy`, `matplotlib`, `seaborn`, `pingouin`, `factor_analyzer`, `scikit-learn`, `statsmodels`, `scipy`

---

# Factors Related to Internet Use in the Czech Republic

An analysis of **European Social Survey Round 10** (ESS10, edition 3.3) data for the **Czech Republic**.

**Aim:** to examine which social characteristics and value orientations are associated with how much time a person spends on the Internet on a typical day.

The analysis is in [`digital_social_contacts.ipynb`](digital_social_contacts.ipynb).

## Data

- **Source:** European Social Survey European Research Infrastructure (ESS ERIC). (2025). *ESS10 — Integrated file, edition 3.3* [Dataset]. Sikt. [https://doi.org/10.21338/ESS10E03_3](https://doi.org/10.21338/ESS10E03_3)
- **Sample:** Czech respondents (`cntry == CZ`); **1,490** observations after missing-value cleaning
- **Outcome:** `netustm` - Internet use on a typical day, in minutes
- **Predictors:** gender, age, happiness, social activity compared with people of the same age, social trust, and four human-value factors

## Analysis

1. **Exploratory data analysis.** Variable selection, type correction, missing-value codes from the codebook, and a *social trust* index as the mean of `ppltrst`, `pplfair`, and `pplhlp`.
2. **Exploratory factor analysis** of 21 Human Values items. Assumptions were checked (KMO, Bartlett’s test, linearity, outliers). Because multivariate normality was violated, factors were extracted with *Principal Axis Factoring* and orthogonal **Varimax** rotation. The Kaiser criterion supported **4 factors** (about **58.8%** of total variance):
   - *Self-Expression & Care for Others*
   - *Hedonism & Achievement*
   - *Conservatism*
   - *Social Conformity*
3. **Linear regression.** The outcome was log-transformed (`log1p`), and inference used heteroscedasticity-robust standard errors (**HC3**). Adjusted **R² = 0.136**; the model is significant overall.

## Main findings

- **Higher** age, self-expression, hedonism, and social trust are associated with **less** time online.
- **Higher** conservatism and happiness are associated with **more** time online.
- People with an **average** level of social activity use the Internet less than those who are much less or much more socially active than their peers.
- **Gender** and **social conformity** are **not** associated with Internet use.

Approximate magnitudes, holding other predictors constant, on the log scale: each additional year of age is linked to about **1.1%** less time online; a one-standard-deviation increase in conservatism, to about **12.4%** more; a one-standard-deviation increase in hedonism, to about **8.9%** less.

## Repository contents

| File | Description |
| --- | --- |
| `digital_social_contacts.ipynb` | main analysis |
| `factor_loadings_varimax.csv` | factor loadings |
| `communalities.csv` | communalities |
| `factor_scores.csv` | factor scores |

## Main libraries used

`pandas`, `numpy`, `matplotlib`, `seaborn`, `pingouin`, `factor_analyzer`, `scikit-learn`, `statsmodels`, `scipy`
