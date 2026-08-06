---
name: canvas-drive-upload
description: Status of Drive notebook upload for Fall 2026 Canvas imscc; drive_links.json now written
metadata:
  type: project
  type: project
  originSessionId: ff66b240-47ea-4760-bde9-f23c9f9a99b2
---

Uploading all ae240 notebooks (M05–M14) to Google Drive so Canvas scripts can generate Colab links via `drive_links.json`.

**Why:** Canvas scripts (`cavasIMporting/update_module05.py` and `update_modules06_14.py`) were switched from GitHub Colab URLs to Drive Colab URLs. They require `drive_links.json` (maps module-relative path → Drive file ID) at repo root.

**How to apply:** When resuming, check whether M08 workflow finished, write `drive_links.json`, then run the Canvas scripts.

## Status at last session end
- All 63 notebooks uploaded to Drive; `drive_links.json` written; imscc built at `/tmp/ae240_fall2026_all_modules_updated.imscc` (95.8 MB)
- **Adversarial validation complete** — all M05–M14 checks passed (remaining test failures are M1–M4/M18 out-of-scope)
- Final fixes in `cavasIMporting/update_modules06_14.py` Step 4c-5:
  - M11: `2025_practiceExam_SOLUTION` → `2026_practiceExam_SOLUTION`
  - M14: `exam3_part2_blank` → `exam3_part2_blank-remove` (flagged for deletion after import)
- **Non-obvious**: homework blank notebooks (M05, M08–M10, M12–M13) are NOT linked as ExternalUrl items — they live in Canvas Assignment HTML descriptions. The SOLUTION ExternalUrls are unpublished module items. Do not add ExternalUrl links for homework blanks.
- **Drive permissions DONE**: all 67 files (root folder + 63 notebooks + subfolders) set to "Anyone with link — Viewer" via `set_drive_permissions.py` using `becca.napolitano@gmail.com` / Cloud project `565283716688`
- Everything committed (commit `994a84f`); `credentials.json`, `token.json`, `*.imscc` in `.gitignore`
- **Only remaining step**: import `cavasIMporting/ae240_fall2026_all_modules_updated.imscc` into Canvas via Settings → Import Course Content → Common Cartridge, then delete `exam3_part2_blank-remove` in M14

## New Drive folder IDs (the real ones, from manual upload)
```
Module_05_introduction_to_python:        1zw7AnMB1utiR2VSDGZpRWk4DKHaKZtRM
Module_06_linear_regression_and_modeling: 1vEKYyJw8em4p7bqsmp_jHKwjdT4d_qkX
Module_07_exam_1:                        1VwFBsxdfu07mpOgv7mqz6mopaHvEaolc
Module_08_dataframes:                    1O_W4-nH-DYLywUhlhhOVP63f6vrv68Dq
Module_09_data_cleaning:                 1I-jKGlhNsyE4B3p03k1A_6j7XZOdsM1E
Module_10_conditionals:                  1SQKakdcRsNzCGiFpqbbiJFe3B26BO7mT
Module_11_exam_2:                        1BNJgDjBP5-9N9eoRrtlgsDDcN1CxUvzF
Module_12_nonLinear:                     1tB6VKIMlF8o2ej0Ynu3pSh6c-dHxC7Wx
Module_13_optimization:                  1sZofLnYDEp5h01YtEe-wogDbGq04Kh4E
Module_14_exam_3:                        1nCiCVhN-3BbdZzs25pieaurG_TBcahBK
Root folder:                             1QEA3N7jo8eD_NMwdLLStoOPY-Wqh6F0B
```

## Drive folder IDs
```
Module_05_introduction_to_python:        17EDbb3kzTbBJf7sBLbROqlxFadbbELU5
Module_06_linear_regression_and_modeling: 17PkXeQONkb2No890qe6oUlNZYgRZ3yf1
Module_07_exam_1:                        1wh7uXMyoAJ9DbaB5o0Kb9qPsbBrR8thy
Module_08_dataframes:                    19qFwtkRXcFHE7Xwyq5NaukGYn3Chmuyp
Module_09_data_cleaning:                 1b6vJn2D7mzq8WkxSkV6id1fVNR4xK6GS
Module_10_conditionals:                  1clFFWzmiGiLRFaSY-WHc1Ca7Dk3XtqcC
Module_11_exam_2:                        1A_ZYoEzvUpa4OTU5pGY_9_a_UnEYfa-O
Module_12_nonLinear:                     1ML03FOzAsJC5xBu6PwL_44iNQY-h_oe5
Module_13_optimization:                  1VeY6o6yXEmtSXxQ95MoljUC0yxNNXZI4
Module_14_exam_3:                        1teodG9VjoTaIYBXIna0ueeOTgPuKEx2o
Root folder:                             1jGPkTy2YOTbBQUDKfELcOazcFucIKeSY
```

## Collected Drive file IDs (M05–M07, M09–M14)
```json
{
  "Module_05_introduction_to_python/1_introPy_session1_v26.ipynb": "1DsgQw6ZGnBQ79up36gUwDsaaas5Cbt66",
  "Module_05_introduction_to_python/1_introPy_session1_v26_SOLUTION.ipynb": "1-pnqvF0ymQ7oai7K9yvBqYjCX22cAHrl",
  "Module_05_introduction_to_python/1_introPy_session2_v26.ipynb": "15Etx2sZjeHHY72ygGnVBHTsrYxNELksK",
  "Module_05_introduction_to_python/1_introPy_session2_v26_SOLUTION.ipynb": "1FxYH-gTTdg__gErfn9e2ZjDwUvQ4Htl8",
  "Module_05_introduction_to_python/2_introPy_homework_v26.ipynb": "1YEVSgKHIwKM2VOw2-6xmKBAxDTlsMzKg",
  "Module_05_introduction_to_python/2_introPy_homework_v26_SOLUTION.ipynb": "1Lpqnsenue19X9rqYtXBGnLHHgQcWaObN",
  "Module_06_linear_regression_and_modeling/1_linReg_notes_v26.ipynb": "1DMb8qbiGsEFzvVUCBKsKIkB6mZ8qe70t",
  "Module_06_linear_regression_and_modeling/1_linReg_notes_v26_SOLUTION.ipynb": "1l-LF3BQ3esWKXczCFK9cdKtH3J-E7R8q",
  "Module_06_linear_regression_and_modeling/2_dataVis_notes_v26.ipynb": "1d5r8ZLELQmVxvbfNiJhM95IuI7nZhzcj",
  "Module_06_linear_regression_and_modeling/2_dataVis_notes_v26_SOLUTION.ipynb": "11GuIUYv0VKqlXHyv56_6yjwgiRAM3vxs",
  "Module_06_linear_regression_and_modeling/3_linReg_dataVis_homework_v26.ipynb": "1o-VG6zSpY9Oxgi_adU6afrSKoBCpo2nq",
  "Module_06_linear_regression_and_modeling/3_linReg_dataVis_homework_v26_SOLUTION.ipynb": "1M_TsHFMmWTO7bMlNvTCaJoPsAA8xq9Ye",
  "Module_07_exam_1/exam1_inClass.ipynb": "1vxSQ3Yjjn9Kj4NlZgpcpEd2EnjALgpL6",
  "Module_07_exam_1/exam_1_part1_v26.ipynb": "17RX8OKIElyjxZ2362GZFk0-CDShKWqtQ",
  "Module_07_exam_1/exam_1_part1_v26_SOLUTION.ipynb": "1WbDZQTjgF72ZTThFJUxr4xw8Ke8wnbcW",
  "Module_07_exam_1/exam_1_part2_v26.ipynb": "1guDVlZc5bGjHoiw-qfdrCuumR5HKhFWZ",
  "Module_07_exam_1/exam_1_part2_v26_SOLUTION.ipynb": "1lORbLdoNt340n5DMrm6ZJoLw5OYUAMoN",
  "Module_07_exam_1/exam_1_practice_v26.ipynb": "1SF8oF-gZPUy1yhNW9rfmPYEOIDxQPfgR",
  "Module_07_exam_1/exam_1_practice_v26_SOLUTION.ipynb": "1Em47kf8guWG8bL1CBIYwxFSSRQLhyqts",
  "Module_07_exam_1/study_guide_extra_help.ipynb": "1khhwMid_t3FquOEz6k0BHI76xtE8N0Ia",
  "Module_09_data_cleaning/1_dataCleaning_v26.ipynb": "1eEzbrZRyxho5CEIipB12SiL0vVucsisU",
  "Module_09_data_cleaning/1_dataCleaning_v26_SOLUTION.ipynb": "1cq4CdxoKZWxcgedzh7s-OChn7XlXdpkm",
  "Module_09_data_cleaning/2_dataCleaning_v26.ipynb": "1D5JgcwPA0JcJ28It4YanVrd-EgUN69rX",
  "Module_09_data_cleaning/2_dataCleaning_v26_SOLUTION.ipynb": "1_eB9PQLaPwPOvFCWq6n2va1-3-s6KAeV",
  "Module_09_data_cleaning/3_dataCleaning_homework_v26.ipynb": "1q6zvuHxl8LeZ4I01LTWnktZE9AFoOD5b",
  "Module_09_data_cleaning/3_dataCleaning_homework_v26_SOLUTION.ipynb": "1plepGNq2gSrfRSaN32ETTIsUee52yTBq",
  "Module_09_data_cleaning/Cultivating_Engineering_Judgement.ipynb": "1IRMNDYvmM9EVX8uk-3OoR0RQ5ceQKEAp",
  "Module_10_conditionals/1_conditionals_session1_v26.ipynb": "1yUVw2cLIMpCHyW--dRWhdrGlu4zKUMSr",
  "Module_10_conditionals/1_conditionals_session1_v26_SOLUTION.ipynb": "18r8HZWyhTAQWAgRg96Ag7FTOZw9Ps5fj",
  "Module_10_conditionals/2_conditionals_session2_v26.ipynb": "1VMpmZcz7_2lziumXw9Qc9QUN-QNufRAt",
  "Module_10_conditionals/2_conditionals_session2_v26_SOLUTION.ipynb": "1bCj5dKNESMSvoUpDow87e7mZgxPDEs0H",
  "Module_10_conditionals/3_conditionals_homework_v26.ipynb": "1rULDNTt6THreOTBMkxg0cgKGfJdxEWe1",
  "Module_10_conditionals/3_conditionals_homework_v26_SOLUTION.ipynb": "1JO4ZWXjwypypxS2SLS7QagoTEnUUnYLv",
  "Module_11_exam_2/exam2_part1_v26.ipynb": "1CuFVE6_bvpwtWSDt7yAU51p_u4XTl-o6",
  "Module_11_exam_2/exam2_part1_v26_SOLUTION.ipynb": "1H4XfYffaxgTNGe3Rg8PySjijNjVUoSo0",
  "Module_11_exam_2/exam2_part2_v26.ipynb": "1mvWqXCMQEUwq1HruANvzVs_aUcxfxoE0",
  "Module_11_exam_2/exam2_part2_v26_SOLUTION.ipynb": "1KwradUzfzVPJ0RImKjTDGDfci7sMoa3X",
  "Module_11_exam_2/exam2_practiceExam_v26.ipynb": "1Xlken2YiDeOy6RPsWZiJss68_emUE7CF",
  "Module_11_exam_2/exam2_practiceExam_v26_SOLUTION.ipynb": "1b-ruYRO3scPnW3bwHi3WK3KHFSzh2DR1",
  "Module_11_exam_2/studyGuide_v26.ipynb": "19Xe6UOOwhYI2J7N7-TQCgQ9kHgDIpt8D",
  "Module_12_nonLinear/1_NonLinear_session1_v26.ipynb": "1F-g_meWkHjdvtRHAgTHuE89zsSBLel2D",
  "Module_12_nonLinear/1_NonLinear_session1_v26_SOLUTION.ipynb": "1WRPUPcUjCgvazSxVp47Hpe6g1IPIDsEo",
  "Module_12_nonLinear/2_NonLinear_session2_v26.ipynb": "1uSGvFsPLBirAGHrFzKZqKmSL25yRGJIS",
  "Module_12_nonLinear/2_NonLinear_session2_v26_SOLUTION.ipynb": "1EbXiFURBsv_0i44CNplzCNchuE-1uiZR",
  "Module_12_nonLinear/3_nonlinear_homework_v26.ipynb": "1YWP1_z5o3RyOdJvgDxBtIIPsaeuDDG15",
  "Module_12_nonLinear/3_nonlinear_homework_v26_SOLUTION.ipynb": "1GtNPdDCZi30iUxB91MASqEe9h3K9toFs",
  "Module_13_optimization/1_optimization_session1_v26.ipynb": "1ANJSnYyCXZwvJov-sReMdCwOI6r3ASpT",
  "Module_13_optimization/1_optimization_session1_v26_SOLUTION.ipynb": "1iodRAWXWs12vxH9cgwVtpQLmLg0tPrBm",
  "Module_13_optimization/2_optimization_session2_v26.ipynb": "1D-gQmHz8mBlfnJQm4iCRA_g7DU9vZGQi",
  "Module_13_optimization/2_optimization_session2_v26_SOLUTION.ipynb": "1zJF-sR5pOw5frSlvsXdiEc-JN7VYzeup",
  "Module_13_optimization/3_optimization_homework_v26.ipynb": "1nuQ9atzdJ9zYlnc0G697wwrAZoLYBSM2",
  "Module_13_optimization/3_optimization_homework_v26_SOLUTION.ipynb": "1ymGfRVOepyPROD153o4mHJCHSkK8o_RX",
  "Module_13_optimization/optimization_extra_cubic_v26.ipynb": "1GliWY_3lc8Dh0CJpRpAHFJIUPlBY5fm8",
  "Module_13_optimization/optimization_extra_cubic_v26_SOLUTION.ipynb": "1O7lN-BMgsHu8D5MjpUWUwWvFycq0sHI3",
  "Module_14_exam_3/exam3_part1_v26.ipynb": "1cWgiRThqmOGxFKpWy06E74roTMfAChr6",
  "Module_14_exam_3/exam3_part1_v26_SOLUTION.ipynb": "1w-WrJBKbopBrPVTLh328hHD5vp3t0GYQ",
  "Module_14_exam_3/exam3_part2_v26.ipynb": "1b5mvXa3B_bR7E05K759t9HeCUrD2fRM9",
  "Module_14_exam_3/exam3_part2_v26_SOLUTION.ipynb": "1rQJJ2ZPch06l0UCCt0TfJmt29XryNORA",
  "Module_14_exam_3/exam_3_practice_v26.ipynb": "1mRQZCcY7JTsHDY6AWM5Msi6DkOhlnjNo",
  "Module_14_exam_3/exam_3_practice_v26_SOLUTION.ipynb": "1pH3bNrYe9HuXkDlrJhqv-ZuW77p29_H6"
}
```

## M08 blocker detail
Large base64 images embedded in markdown *source* cells (not outputs):
- `2_dataVis_notes_v26.ipynb` (545KB): cells of 166KB, 136KB, 106KB, 70KB each
- `2_dataVis_notes_v26_SOLUTION.ipynb` (784KB): similar
- Other M08 files (~204–220KB each) may also be too large

If `wjlf1ziqc` still fails, options:
1. User manually uploads M08 to Drive folder `19qFwtkRXcFHE7Xwyq5NaukGYn3Chmuyp`, then use MCP search to get IDs
2. Set env var `CLAUDE_CODE_MAX_OUTPUT_TOKENS=200000` and restart Claude Code, then retry
3. Fix OAuth (`credentials.json` + add `rjn5308@psu.edu` as test user in Cloud project 366849977595)

## Also note
- `credentials.json` and `token.json` should be added to `.gitignore`
- Uncommitted changes: `cavasIMporting/update_module05.py` and `update_modules06_14.py` (switched from GitHub to Drive Colab URLs)
