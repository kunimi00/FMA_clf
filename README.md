### FMA Genre Classification 실습

[`fma_small.zip`]:    https://os.unil.cloud.switch.ch/fma/fma_small.zip
[`fma_medium.zip`]:   https://os.unil.cloud.switch.ch/fma/fma_medium.zip
[`fma_large.zip`]:    https://os.unil.cloud.switch.ch/fma/fma_large.zip
[`fma_full.zip`]:     https://os.unil.cloud.switch.ch/fma/fma_full.zip

**[`fma_small.zip`]**: 8,000 tracks of 30s, 8 balanced genres (GTZAN-like) (7.2 GiB)
**[`fma_medium.zip`]**: 25,000 tracks of 30s, 16 unbalanced genres (22 GiB)
**[`fma_large.zip`]**: 106,574 tracks of 30s, 161 unbalanced genres (93 GiB)
**[`fma_full.zip`]**: 106,574 untrimmed tracks, 161 unbalanced genres (879 GiB)

[`fma_metadata.zip`]: https://os.unil.cloud.switch.ch/fma/fma_metadata.zip

* `tracks.csv`: per track metadata such as ID, title, artist, genres, tags and play counts, for all 106,574 tracks.
* `genres.csv`: all 163 genres with name and parent (used to infer the genre hierarchy and top-level genres).
* `features.csv`: common features extracted with [librosa].
* `echonest.csv`: audio features provided by [Echonest] (now [Spotify]) for a subset of 13,129 tracks.



Clone the repository.

    ```sh
    git clone https://github.com/kunimi00/FMA_clf
    cd FMA_clf
    ```


Install dependencies.

    ```sh
    pip install --upgrade pip setuptools wheel
    pip install numpy
    pip install -r requirements.txt
    ```


Download some data, verify its integrity, and uncompress the archives.

    ```sh
    cd data

    curl -O https://os.unil.cloud.switch.ch/fma/fma_metadata.zip
    curl -O https://os.unil.cloud.switch.ch/fma/fma_small.zip
    curl -O https://os.unil.cloud.switch.ch/fma/fma_medium.zip
    curl -O https://os.unil.cloud.switch.ch/fma/fma_large.zip
    curl -O https://os.unil.cloud.switch.ch/fma/fma_full.zip

    echo "f0df49ffe5f2a6008d7dc83c6915b31835dfe733  fma_metadata.zip" | sha1sum -c -
    echo "ade154f733639d52e35e32f5593efe5be76c6d70  fma_small.zip"    | sha1sum -c -
    echo "c67b69ea232021025fca9231fc1c7c1a063ab50b  fma_medium.zip"   | sha1sum -c -
    echo "497109f4dd721066b5ce5e5f250ec604dc78939e  fma_large.zip"    | sha1sum -c -
    echo "0f0ace23fbe9ba30ecb7e95f763e435ea802b8ab  fma_full.zip"     | sha1sum -c -

    unzip fma_metadata.zip
    unzip fma_small.zip
    unzip fma_medium.zip
    unzip fma_large.zip
    unzip fma_full.zip

    cd ..
    ```
