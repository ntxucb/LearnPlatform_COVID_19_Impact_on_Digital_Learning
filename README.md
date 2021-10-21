# LearnPlatform_COVID_19_Impact_on_Digital_Learning :mortar_board:

# Project Description :globe_with_meridians:
We include the analysis notebook of the [COVID_19_Impact_on_Digital_Learning competition](https://www.kaggle.com/c/learnplatform-covid19-impact-on-digital-learning). The Challenge consisted of exploring (1) the state of digital learning in 2020 and (2) how the engagement of digital learning relates to factors such as district demographics, broadband access, and state/national level policies and events.

The questions we did ourselves that relate to the problem statement were:

* What is the picture of digital connectivity and engagement in 2020?<br>
* What is the effect of the COVID-19 pandemic on online and distance learning, and how might this also evolve in the future?<br>
* How does student engagement with different types of education technology change over the course of the pandemic?<br>
* How does student engagement with online learning platforms relate to different geography? Demographic context (e.g., race/ethnicity)? Learning context?<br>

* :arrow_down: Data can be downloaded [Here](https://www.kaggle.com/lordofmont/learnplatform-covid-19-impact/data) :arrow_down:


# Data Description :cd:

The engagement data are based on [LearnPlatform](https://learnplatform.com/)’s Student Chrome Extension. The extension collects page load events of over 10K education technology products in our product library, including websites, apps, web apps, software programs, extensions, ebooks, hardwares, and services used in educational institutions. The engagement data have been aggregated at school district level, and each file represents data from one school district. The product file includes information about the characteristics of the top 372 products with most users in 2020. The district file includes information about the characteristics of school districts, including data from [National Center for Education Statistics (NCES)](https://nces.ed.gov/), [The Federal Communications Commission (FCC)](https://www.fcc.gov/), and [Edunomics Lab](https://edunomicslab.org/). In addition to the files provided, we encourage you to use other public data sources such as examples listed below.

## File Structure :open_file_folder:

The organization of data sets is described below:

```
Root/
  -engagement_data/
    -1000.csv
    -1039.csv
    -...
  -districts_info.csv
  -products_info.csv
  -README.md

```

## Data Definition :clipboard:


### Engagement data
The engagement data are aggregated at school district level, and each file in the folder `engagement_data` represents data from one school district. The 4-digit file name represents `district_id` which can be used to link to district information in `district_info.csv`. The `lp_id` can be used to link to product information in `product_info.csv`.

| Name | Description |
| :--- | :----------- |
| time | date in "YYYY-MM-DD" |
| lp_id | The unique identifier of the product |
| pct_access | Percentage of students in the district have at least one page-load event of a given product and on a given day |
| engagement_index | Total page-load events per one thousand students of a given product and on a given day |


### District information data

The district file `districts_info.csv` includes information about the characteristics of school districts, including data from [NCES](https://nces.ed.gov/) (2018-19), [FCC](https://www.fcc.gov/) (Dec 2018), and [Edunomics Lab](https://edunomicslab.org/). In this data set, we removed the identifiable information about the school districts. We also used an open source tool [ARX](https://arx.deidentifier.org/) [(Prasser et al. 2020)](https://onlinelibrary.wiley.com/doi/full/10.1002/spe.2812) to transform several data fields and reduce the risks of re-identification. For data generalization purposes some data points are released with a range where the actual value falls under. Additionally, there are many missing data marked as 'NaN' indicating that the data was suppressed to maximize anonymization of the dataset. 

| Name | Description |
| :--- | :----------- |
| district_id | The unique identifier of the school district |
| state | The state where the district resides in |
| locale | NCES locale classification that categorizes U.S. territory into four types of areas: City, Suburban, Town, and Rural. See [Locale Boundaries User's Manual](https://eric.ed.gov/?id=ED577162) for more information. |
| pct_black/hispanic | Percentage of students in the districts identified as Black or Hispanic based on 2018-19 NCES data |
| pct_free/reduced | Percentage of students in the districts eligible for free or reduced-price lunch based on 2018-19 NCES data |
| county_connections_ratio | `ratio` (residential fixed high-speed connections over 200 kbps in at least one direction/households) based on the county level data from FCC From 477 (December 2018 version). See [FCC data](https://www.fcc.gov/form-477-county-data-internet-access-services) for more information. |
| pp_total_raw | Per-pupil total expenditure (sum of local and federal expenditure) from Edunomics Lab's National Education Resource Database on Schools (NERD$) project. The expenditure data are school-by-school, and we use the median value to represent the expenditure of a given school district. |


### Product information data
The product file `products_info.csv` includes information about the characteristics of the top 372 products with most users in 2020. The categories listed in this file are part of LearnPlatform's product taxonomy. Data were labeled by our team. Some products may not have labels due to being duplicate, lack of accurate url or other reasons.

| Name | Description |
| :--- | :----------- |
| LP ID| The unique identifier of the product |
| URL | Web Link to the specific product |
| Product Name | Name of the specific product |
| Provider/Company Name | Name of the product provider |
| Sector(s) | Sector of education where the product is used |
| Primary Essential Function | The basic function of the product. There are two layers of labels here. Products are first labeled as one of these three categories: LC = Learning & Curriculum, CM = Classroom Management, and SDO = School & District Operations. Each of these categories have multiple sub-categories with which the products were labeled |
