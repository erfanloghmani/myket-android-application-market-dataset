# Myket Android Application Install Dataset

This dataset contains information on application install interactions of users in the [Myket](https://myket.ir/) android application market. The dataset was created for the purpose of evaluating interaction prediction models, requiring user and item identifiers along with timestamps of the interactions. Hence, the dataset can be used for interaction prediction and building a recommendation system. Furthermore, the data forms a dynamic network of interactions, and we can also perform network representation learning on the nodes in the network, which are users and applications.

## Data Creation

The dataset was initially generated by the Myket data team, and later cleaned and subsampled by Erfan Loghmani a master student at Sharif University of Technology at the time. The data team focused on a two-week period and randomly sampled 1/3 of the users with interactions during that period. They then selected install and update interactions for three months before and after the two-week period, resulting in interactions spanning about 6 months and two weeks.

We further subsampled and cleaned the data to focus on application download interactions. We identified the top 8000 most installed applications and selected interactions related to them. We retained users with more than 32 interactions, resulting in 280,391 users. From this group, we randomly selected 10,000 users, and the data was filtered to include only interactions for these users. The detailed procedure can be found in [here](create_data.ipynb).

## Data Structure

The dataset has two main files.

- `myket.csv`: This file contains the interaction information and follows the same format as the datasets used in the "[JODIE: Predicting Dynamic Embedding Trajectory in Temporal Interaction Networks](https://github.com/claws-lab/jodie)" (ACM SIGKDD 2019) project. However, this data does not contain state labels and interaction features, resulting in associated columns being all zero.
- `app_info_sample.csv`: This file comprises features associated with applications present in the sample. For each individual application, information such as the approximate number of installs, average rating, count of ratings, and category are included. These features provide insights into the applications present in the dataset.

Additionally, the `data_int_index` directory contains dataset files where app_names and user_ids have been converted into integers that commence from zero and increment by one. This numeric format can be more convenient for usage. The directory also includes mappings linking the previous identifiers to the new ones. Furthermore, a numpy version of `app_info_sample.csv` is available, containing numerical features for each app and dummy variables for categories.

## Dataset Details

- Total Instances: 694,121 install interaction instances
- Instances Format: Triplets of user_id, app_name, timestamp
- 10,000 users and 7,988 android applications
- Item features for 7,606 applications

For a detailed summary of the data's statistics, including information on users, applications, and interactions, please refer to the Python notebook available at [summary-stats.ipynb](summary-stats.ipynb). The notebook provides an overview of the dataset's characteristics and can be helpful for understanding the data's structure before using it for research or analysis.

### Top 20 Most Installed Applications

| Package Name                       | Count of Interactions |
| ---------------------------------- | --------------------- |
| com.instagram.android              | 15292                 |
| ir.resaneh1.iptv                   | 12143                 |
| com.tencent.ig                     | 7919                  |
| com.ForgeGames.SpecialForcesGroup2 | 7797                  |
| ir.nomogame.ClutchGame             | 6193                  |
| com.dts.freefireth                 | 6041                  |
| com.whatsapp                       | 5876                  |
| com.supercell.clashofclans         | 5817                  |
| com.mojang.minecraftpe             | 5649                  |
| com.lenovo.anyshare.gps            | 5076                  |
| ir.medu.shad                       | 4673                  |
| com.firsttouchgames.dls3           | 4641                  |
| com.activision.callofduty.shooter  | 4357                  |
| com.tencent.iglite                 | 4126                  |
| com.aparat                         | 3598                  |
| com.kiloo.subwaysurf               | 3135                  |
| com.supercell.clashroyale          | 2793                  |
| co.palang.QuizOfKings              | 2589                  |
| com.nazdika.app                    | 2436                  |
| com.digikala                       | 2413                  |

## Comparison with SNAP Datasets

The Myket dataset introduced in this repository exhibits distinct characteristics compared to the real-world datasets used by the project. The table below provides a comparative overview of the key dataset characteristics:

| Dataset         | #Users           | #Items          | #Interactions | Average Interactions per User | Average Unique Items per User |
| --------------- | ---------------- | --------------- | ------------- | ----------------------------- | ----------------------------- |
| **Myket** | **10,000** | **7,988** | 694,121       | 69.4                          | 54.6                          |
| LastFM          | 980              | 1,000           | 1,293,103     | 1,319.5                       | 158.2                         |
| Reddit          | **10,000** | 984             | 672,447       | 67.2                          | 7.9                           |
| Wikipedia       | 8,227            | 1,000           | 157,474       | 19.1                          | 2.2                           |
| MOOC            | 7,047            | 97              | 411,749       | 58.4                          | 25.3                          |

The Myket dataset stands out by having an ample number of both users and items, highlighting its relevance for real-world, large-scale applications. Unlike LastFM, Reddit, and Wikipedia datasets, where users exhibit repetitive item interactions, the Myket dataset contains a comparatively lower amount of repetitive interactions. This unique characteristic reflects the diverse nature of user behaviors in the Android application market environment.

## Citation

If you use this dataset in your research, please cite the following [preprint](https://arxiv.org/abs/2308.06862):

```
@misc{loghmani2023effect,
      title={Effect of Choosing Loss Function when Using T-batching for Representation Learning on Dynamic Networks}, 
      author={Erfan Loghmani and MohammadAmin Fazli},
      year={2023},
      eprint={2308.06862},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```
