# Understanding Relevance Judgments in Legal Case Retrieval

Data in the paper *"Understanding Relevance Judgments in Legal Case Retrieval"* (accepted by TOIS, Transactions on Information Systems).
This paper conducted a laboratory user study to inspect multiple factors, including domain expertise, query case complexity. Beyond relevance judgments, this study collected users' feedback, efficienty and utility measures, text annotations, and semi-structured reasons. The query and candidate cases were selected based on [LeCaRD](https://img.shields.io/github/license/myx666/LeCaRD). The participants of the user study are anonymized in this dataset.

## Dataset Structure

`/data` is the root directory for all data. The main files are structured as:

```
data
├── basic_measures.csv
├── highlights.json
├── semi_structrured_reasons.csv
└── tasks // cases used in the user study
    ├── cadidate_cases 
    └── query_cases.json
```

## Details

`tasks/query_cases.json` includes all of the used query cases. Each line is a query case. The index of line (begin with 0) also represents the task ID.

`tasks/candidate_cases/` includes the selected candidated cases. Each file is a case. The file_name also represents the case ID. Each case includes the following information:

```
{
    'cid': XXX, // unique id in LeCaRD, not used in this study
    'qw': XXX, // full text of the case
    'label': int, // [1, 4], relevance label
}
```

`basic_measures.csv` contains multi-aspect features and measures extracted from the user study logs. Please refer to **RQ1** for main results and analyses. The columns denote:

```
user: anonymized username, 
u_type: domain expertise of user, //c - criminal, nc - non-criminal, nl - non-legal
task_id: the ID of experimental task,
q_type: whether the query includes multiple causes, // 0 - single, 1 - multiple
cid: the ID of the candidate case, // equals to file name of the case
label: relevance label given by LeCaRD,
relevance: relevance judgments given by the user,
pre-difficulty: pre-task difficulty reported by the user,
post-difficulty: post-task difficulty reported by the user,
confidence: post-task confidence reported by the user,
dwell: the time of making relevance judgments (in seconds)
```

`semi_structrured_reasons.csv` contains users' semi-structured reasons for their relevance judgments. Six aspects are included, i.e., key elements (要件事实), key circumstances (案情事实), issue (争议焦点), law (法律适用), cause (案由), story (其他案情). The suffix *_imp*, *_q*, *_c* denotes the importance score, the contents in the query, the contents in the candidate case, respectively.

`highlights.json` includes highlight annotations of the cases. Each line is a dict, including:

```
{
    'task_id': the ID of experimental task,
    'user': anonymized username,
    'doc_type': query / case, // denotes query case or candidate case
    'html': the case text with highlight annotations
}
```
Note that the text surrounded by `<span></span>` is highlighted by the user. 

## Citation

To Appear.


## Connect

For more infomation, please refer to our paper [Understanding Relevance Judgments in Legal Case Retrieval](https://dl.acm.org/doi/pdf/10.1145/3569929). If you have any questions, please email [Yunqiu Shao](shaoyq18@mails.tsinghua.edu.cn). 

