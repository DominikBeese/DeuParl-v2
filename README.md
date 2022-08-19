[![](https://img.shields.io/github/license/DominikBeese/DeuParl-v2?label=License)](/LICENSE)
# DeuParl v2
Plenary protocols from the German [_Reichstag_](/Reichstag%20Data) (1867-1945) and [_Bundestag_](/Bundestag%20Data) (1949-2022).

<img src="https://user-images.githubusercontent.com/111588769/185678076-f97425a8-5b06-4d4c-b17f-dd3bffabfd8a.png" alt="SittingsPerYear-Histplot" width="400">

We obtain data from two sources: (i) [_Open Data_](https://www.bundestag.de/services/opendata) where the German parliament publishes all plenary protocols from the _Bundestag_ (_en_.: federal diet); and  (ii) [_Reichstagsprotokolle_](https://www.reichstagsprotokolle.de/) that contains all _Reichstag_ (_en_.: imperial diet) protocols, distributed by the _Bayerische Staatsbibliothek_; we use the OCR-scanned version from [Walter et al. (2021)](https://tudatalib.ulb.tu-darmstadt.de/handle/tudatalib/2889).

For the _Reichstag_ data, we apply preprocessing steps similar to [Walter et al. (2021)](https://github.com/umanlp/crosstemporal_bias), but keep German umlauts. We then automatically split the data into individual sittings and collect metadata like the date, period and session number of each sitting, which we manually checked and corrected. The _Reichstag_ data is subdivided into the seven time periods listed in the table below. The abbreviations in brackets indicate the `type` as used in our dataset.

| Period                                    | Years     |
|-------------------------------------------|-----------|
| Konstituierender Reichstag [`k`]          | 1867      |
| Reichstag (Norddeutscher Bund) [`ndb`]    | 1867-1870 |
| Zollparlament [`zp`]                      | 1886-1870 |
| Reichstag (Deutsches Kaiserreich) [`dkr`] | 1871-1918 |
| Nationalversammlung [`nv`]                | 1919-1920 |
| Reichstag (Weimarer Republik) [`wr`]      | 1919-1933 |
| Reichstag (Nationalsozialismus) [`ns`]    | 1933-1945 |

Both directories contain a `details.json` file with the following information for each sitting:

| Key      | Value  | Description                                |
| ---------|--------|--------------------------------------------|
| `era`    | string | `rt` for Reichstag _or_ `bt` for Bundestag |
| `type`   | string | only for Reichstag data, see table above   |
| `period` | number | election period                            |
| `no`     | number | number of the sitting                      |
| `year`   | number | year of the sitting                        |
| `month`  | number | month of the sitting                       |
| `day`    | number | day of the sitting                         |


## Citation
```
@article{FairGer,
          title = "{F}air{G}er: Using {NLP} to Measure Support for Women and Migrants in 155 Years of German Parliamentary Debates",
         author = "Dominik Beese and Ole P{\"u}tz and Steffen Eger",
           year = "2022",
         eprint = "2210.04359",
  archivePrefix = "arXiv",
   primaryClass = "cs.CL"
}
```
> **Abstract:** We measure support with women and migrants in German political debates over the last 155 years. To do so, we (1) provide a gold standard of 1205 text snippets in context, annotated for support with our target groups, (2) train a BERT model on our annotated data, with which (3) we infer large-scale trends. These show that support with women is stronger than support with migrants, but both have steadily increased over time. While we hardly find any direct anti-support with women, there is more polarization when it comes to migrants. We also discuss the difficulty of annotation as a result of ambiguity in political discourse and indirectness, i.e., politicians' tendency to relate stances attributed to political opponents. Overall, our results indicate that German society, as measured from its political elite, has become fairer over time.
