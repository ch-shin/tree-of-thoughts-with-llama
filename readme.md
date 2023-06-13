# Tree of Thoughts (ToT) with LLaMA
> ***Note***: *This is a forked repository from the Official Repo of Tree of Thoughts (ToT) cited below. This implementation utilizes LLaMA (Large Language Model Meta AI) for experimental purposes, which deviates from the original implementation using GPT - OpenAI API. Please refer to the link to the official repo for the original implementational details.*

# Forked from: Official Repo of Tree of Thoughts (ToT)
[![DOI](https://zenodo.org/badge/642099326.svg)](https://zenodo.org/badge/latestdoi/642099326)

**IMPORTANT Note: https://github.com/kyegomez/tree-of-thoughts is NOT the official implementation to replicate the results in the paper (see https://github.com/ysymyth/tree-of-thought-llm/issues/17).**

![teaser](teaser.png)

Official implementation for paper [Tree of Thoughts: Deliberate Problem Solving with Large Language Models](https://arxiv.org/abs/2305.10601) with code, prompts, model outputs.
Also check [its tweet thread](https://twitter.com/ShunyuYao12/status/1659357547474681857) in 1min.


Please cite the paper and star this repo if you use ToT and find it interesting/useful. Thanks!

```bibtex
@misc{yao2023tree,
      title={{Tree of Thoughts}: Deliberate Problem Solving with Large Language Models}, 
      author={Shunyu Yao and Dian Yu and Jeffrey Zhao and Izhak Shafran and Thomas L. Griffiths and Yuan Cao and Karthik Narasimhan},
      year={2023},
      eprint={2305.10601},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```



## Setup


## Experiments

Run experiments via ``sh scripts/{game24, text, crosswords}/{standard_sampling, cot_sampling, bfs}.sh``, except in crosswords we use a DFS algorithm for ToT, which can be run via ``scripts/crosswords/search_crosswords-dfs.ipynb``.

The very simple ``run.py`` implements the ToT + BFS algorithm, as well as the naive IO/CoT sampling. Some key arguments:

- ``--naive_run``: if True, run naive IO/CoT sampling instead of ToT + BFS.
-  ``--prompt_sample`` (choices=[``standard``, ``cot``]): sampling prompt
- ``--method_generate`` (choices=[``sample``, ``propose``]): thought generator, whether to sample independent thoughts (used in Creative Writing) or propose sequential thoughts (used in Game of 24)
- ``--method_evaluate`` (choices=[``value``, ``vote``]): state evaluator, whether to use the value states independently (used in Game of 24) or vote on states together (used in Creative Writing)
- ``--n_generate_sample``: number of times to prompt for thought generation
- ``--n_evaluate_sample``: number of times to prompt for state evaluation
- ``--n_select_sample``: number of states to keep from each step (i.e. ``b`` in the paper's ToT + BFS algorithm)


