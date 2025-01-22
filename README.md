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
@inproceedings{kostikova-etal-2024-fine,
	title = {Fine-Grained Detection of Solidarity for Women and Migrants in 155 Years of {G}erman Parliamentary Debates},
	author = {Kostikova, Aida and Beese, Dominik and Paassen, Benjamin and P{\"u}tz, Ole and Wiedemann, Gregor and Eger, Steffen},
	year = 2024,
	month = 11,
	booktitle = {Proceedings of the 2024 Conference on Empirical Methods in Natural Language Processing},
	publisher = {Association for Computational Linguistics},
	address = {Miami, Florida, USA},
	pages = {5884--5907},
	doi = {10.18653/v1/2024.emnlp-main.337},
	url = {https://aclanthology.org/2024.emnlp-main.337/},
	editor = {Al-Onaizan, Yaser and Bansal, Mohit and Chen, Yun-Nung},
}
```
> **Abstract:** Solidarity is a crucial concept to understand social relations in societies. In this study, we investigate the frequency of (anti-)solidarity towards women and migrants in German parliamentary debates between 1867 and 2022. Using 2,864 manually annotated text snippets, we evaluate large language models (LLMs) like Llama 3, GPT-3.5, and GPT-4. We find that GPT-4 outperforms other models, approaching human annotation accuracy. Using GPT-4, we automatically annotate 18,300 further instances and find that solidarity with migrants outweighs anti-solidarity but that frequencies and solidarity types shift over time. Most importantly, group-based notions of (anti-)solidarity fade in favor of compassionate solidarity, focusing on the vulnerability of migrant groups, and exchange-based anti-solidarity, focusing on the lack of (economic) contribution. This study highlights the interplay of historical events, socio-economic needs, and political ideologies in shaping migration discourse and social cohesion.
