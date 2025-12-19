%%% Intro.tex ---
%%
%% Filename: Intro.tex
%% Description: Introduction chapter for the Master's Thesis
%% Author: Berkay Orhan
%% Maintainer: Berkay Orhan
%% Created: Tue Nov 25 2025
%% Version: 1.0
%% Last-Updated: Tue Nov 25 2025
%% By: Berkay Orhan
%% Update #: 1
%% URL:
%% Keywords: Thesis, Introduction, RAG, Agentic, Testing
%% Compatibility: LaTeX
%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%%% Commentary:
%%
%%
%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%%% Change log:
%%
%%
%% RCS $Log$
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%%% Code:


\chapter{Introduction}
\label{cha:introduction}

In the domain of large-scale enterprise software development, the velocity of feature delivery is a critical competitive advantage. Modern Continuous Integration and Continuous Deployment (CI/CD) pipelines have enabled rapid iteration cycles, but they simultaneously impose significant demands on quality assurance processes \cite{graham2012experiences}.

\section{Background}
\label{sec:background}

A critical bottleneck in modern CI/CD workflows is \textit{test scope analysis}. In this thesis, we define test scope analysis as the activity of identifying and recommending relevant legacy test cases for verification when a new feature, change request, or defect fix is introduced \cite{hemmati2013achieving}. This differs from traditional Regression Test Selection (RTS), which typically focuses on code-coverage-based filtering of a test suite for automated execution \cite{rothermel1996analyzing, yoo2012regression}. Instead, this work addresses the \textit{Test Case Recommendation} problem \cite{Wang2024SoftwareTesting}: supporting engineers in the semantic discovery of tests that may not be directly linked via static traces but are contextually relevant to the change. Evaluation of such retrieval systems typically relies on standard information retrieval metrics, such as Precision@k (accuracy of top-k results), Recall@k (proportion of relevant items found), and Mean Average Precision (MAP) \cite{manning2008introduction}.

\section{Motivation}
\label{sec:motivation}

For large organizations, maintaining high test coverage while avoiding redundant execution is a complex optimization problem. When a new artifact, such as a user story or bug ticket, is introduced, test engineers must navigate vast repositories of test cases to identify existing coverage and potential gaps \cite{8054871}. Historically, this retrieval process has relied on keyword-based search or the manual inspection of static trace links. However, these traditional methods are increasingly brittle; they often fail to capture the semantic nuance of natural language requirements or the complex, graph-like dependencies between system components \cite{wang2022systematic, antoniol2025recovering}. As software systems grow in complexity, the "semantic gap" between unstructured change descriptions (e.g., "fix race condition in handover") and structured test cases (e.g., "TC\_HO\_001") widens, leading to inefficient scoping, missed defects, and increased maintenance costs \cite{fauzan2021different}.

Recent advancements in Large Language Models (LLMs), which are AI models capable of understanding and generating human-like text, and Retrieval-Augmented Generation (RAG), a technique that enhances LLMs by fetching relevant information from external data sources \cite{lewis2021retrievalaugmentedgenerationknowledgeintensivenlp}, offer promising avenues for bridging this semantic gap \cite{fan2023large, hou2024large}. Simultaneously, Knowledge Graphs (KGs), structured representations of interconnected entities and their relationships, provide a structured means to model the intricate relationships between requirements, code, and tests \cite{kesri2021autokg, radhakrishnan2023create}.

The primary problem addressed in this thesis is the inefficiency and inaccuracy of current test scope analysis methods in large-scale software engineering contexts. Traditional keyword search approaches lack the semantic understanding required to match high-level requirements with low-level test steps, frequently resulting in low recall (missing relevant tests) or low precision (retrieving irrelevant tests).

While standard RAG approaches improve semantic matching, they often suffer from precision errors (retrieving plausible but incorrect context) and "hallucinations" (generative errors where the model invents non-existent facts or test names) \cite{Wang2024SoftwareTesting}. Furthermore, flat RAG retrieval fails to account for the structural context inherent in software artifacts (e.g., inheritance, trace links, execution history). Conversely, purely graph-based methods struggle to effectively process the unstructured free text found in change logs and user stories \cite{cheng2025survey}. Consequently, there is a lack of integrated solutions that leverage the combined strengths of \textit{vector-based semantic retrieval} and \textit{graph-based structural reasoning}, often referred to as \textit{GraphRAG} \cite{edge2025localglobalgraphrag}, to provide accurate and explainable test scope recommendations.

However, a static GraphRAG pipeline, where a query is simply converted to a vector, matched against a graph, and summarized, remains insufficient for complex software engineering tasks. Such pipelines fail when the initial user intent is ambiguous or requires multi-step investigation (e.g., "Check if this change affects the billing module, and if so, find tests for the legacy payment gateway"). A static retrieval process cannot decompose this intent, perform intermediate lookups to refine the search criteria, or reason about the absence of information. To address this, an \textit{agentic architecture} is required \cite{yao2023reactsynergizingreasoningacting}. An agentic architecture is defined as a system where autonomous software agents perceive their environment, reason about how to achieve a goal, and orchestrate the execution of tools to solve complex tasks. By combining these technologies into a system where autonomous AI agents orchestrate retrieval and reasoning loops, there is potential to transform test scope analysis from a manual, error-prone task into an automated, explainable, and highly accurate process \cite{fuchss2025lissa}.

\section{Aim}
\label{sec:aim}

The aim of this thesis is to design and evaluate an agent-orchestrated RAG and Knowledge Graph architecture for test scope analysis. This will involve the implementation of a prototype system to determine the effectiveness of this hybrid approach in automating the retrieval of relevant legacy test cases, identifying coverage gaps, and providing explainable rationales for its recommendations, thereby increasing practical utility for software practitioners, as validated through qualitative feedback from Ericsson engineers in a live or simulated environment.

\section{Research questions}
\label{sec:research-questions}

To fulfill the aim, the following research questions have been formulated:

\begin{itemize}
    \item \textbf{RQ1:} What ontology design is required to model the semantic dependencies between unstructured requirements and structured test artifacts within a Knowledge Graph to enable semantic retrieval?
    \item \textbf{RQ2:} To what extent does an agent-orchestrated GraphRAG approach improve retrieval accuracy compared to standard keyword-based and vector-only RAG methods?
    \item \textbf{RQ3:} To what extent do software practitioners at Ericsson find the automated recommendations accurate and the provided justifications sufficient for decision-making?
\end{itemize}

\section{Delimitations}
\label{sec:delimitations}

This study is delimited to the context of Ericsson’s internal software development environment.
\begin{itemize}
    \item \textbf{Data Scope:} The study will utilize specific datasets provided by Ericsson, including structured test management data (requirements, trace links) and unstructured test case descriptions.
    \item \textbf{Functional Scope:} The system focuses exclusively on \textit{Test Scope Analysis} (identifying relevant existing tests) and does not include the automatic generation of new test cases or the execution of tests.
\end{itemize}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%% Intro.tex ends here


%%% Local Variables:
%%% mode: latex
%%% TeX-master: "student_thesis"
%%% End:
