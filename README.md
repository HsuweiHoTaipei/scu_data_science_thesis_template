# 東吳大學資料科學系碩士論文 LaTeX 範本

這是一份專為東吳大學資料科學系碩士班設計的學位論文 LaTeX 範本。它整合了學術論文所需的各項專業排版功能，並特別針對資料科學領域的需求進行了強化。

---

### 來自學長的愛 ❤️

嗨，學弟妹們！

還在為 Word 的排版、跑掉的圖表、混亂的參考文獻格式而煩惱嗎？畢業前夕，時間應該花在最重要的研究內容上，而不是跟文書處理軟體搏鬥。

這份 LaTeX 範本是我（與 AI 助教）集結了論文寫作過程中所有經驗與踩過的坑，為你們量身打造的。它的目標只有一個：**讓你們可以專注於內容，排版的事交給程式碼就好。**

從雙面列印的書溝、自動化的目錄與頁碼，到資料科學必備的演算法、程式碼、縮寫表，所有你想得到跟想不到的細節，這裡都幫你準備好了。

希望這份範本能成為你們畢業路上的一大助力。祝大家研究順利，準時畢業！

---

## ✨ 功能特色

- **符合學術規範**：完整支援雙面列印、非對稱頁邊距（裝訂邊加寬）、章節從右頁開始。
- **全自動化**：
  - **頁碼**：前言（羅馬數字）、正文（阿拉伯數字）自動切換。
  - **目錄**：自動生成專業的目錄、圖目錄、表目錄。
  - **參考文獻**：支援 APA 格式，使用 BibTeX 自動排序與格式化。
- **模組化管理**：
  - **開關式設計**：可一鍵切換是否顯示「浮水印」或插入「口試審定頁」、「國圖授權頁」，方便草稿與最終版管理。
  - **檔案分離**：論文內容 (`.tex`) 與參考文獻 (`.bib`) 分離，結構清晰。
- **資料科學特化**：
  - **演算法/偽代碼**：使用標準格式清晰呈現演算法。
  - **程式碼區塊**：支援語法高亮 (Syntax Highlighting) 的程式碼排版。
  - **名詞縮寫表**：自動管理論文中的縮寫 (如 NLP, CNN)，並生成對照表。
  - **子圖與智慧引用**：輕鬆並列多張圖片，並使用 `\cref` 智慧引用，自動產生「圖 1.1」或「表 2.3」。

## 🚀 快速上手

### 1. 環境設定

你需要一個 LaTeX 編譯環境。推薦以下兩種方式：

- **本地端 (推薦)**：
  1.  安裝 TeX 發行版：TeX Live (跨平台) 或 MiKTeX (Windows)。
  2.  安裝編輯器：Visual Studio Code + LaTeX Workshop 擴充套件。
- **雲端**：
  - 直接使用 Overleaf 平台，上傳所有檔案即可開始，無需安裝。

**重要**：本範本使用 `xeCJK` 處理中文，請務必使用 **XeLaTeX** 引擎進行編譯。

### 2. 檔案結構

```
your-thesis/
├── dasdan.tex          # 主檔案，所有設定與論文結構都在這裡
├── references.bib      # 參考文獻資料庫
├── figures/
│   └── watermark.jpg   # 範例圖片/浮水印(請到圖書館下載新版本)
├── approval_page.pdf   # (需自備) 口試委員審定頁掃描檔
└── ncl_authorization.pdf # (需自備) 國家圖書館授權頁掃描檔
```

### 3. 開始撰寫

1.  **修改個人資訊**：打開 `dasdan.tex`，在 `\begin{titlepage}` 環境中修改你的論文題目、姓名、指導教授等資訊。
2.  **新增參考文獻**：打開 `references.bib`，將你引用的文獻以 BibTeX 格式貼入。Google Scholar 或 Zotero 等工具都能輕鬆匯出此格式。
3.  **開始寫作**：在 `dasdan.tex` 中找到 `\chapter{緒論}` 等章節標記，開始你的論文寫作之旅！
4.  **編譯**：使用 XeLaTeX 編譯 `dasdan.tex`。**請務必編譯 2-3 次**，以確保目錄、引用、頁碼都正確更新。

## 📝 使用詳解

### 基礎設定 (在 `dasdan.tex` 開頭)

- **最終印刷模式**：
  ```latex
  \finalprintfalse % 改為 \finalprinttrue 才會包含審定頁與授權頁
  ```
  平時設為 `false` 避免編譯錯誤。定稿時，將簽名完成的審定頁與授權頁掃描成 PDF，並將此開關設為 `true`。

- **浮水印開關**：
  ```latex
  \watermarkfalse % 改為 \watermarktrue 即可在背景顯示校徽浮水印
  ```

### 撰寫內容

#### 參考文獻引用

在 `references.bib` 中加入你的文獻，例如：
```bibtex
@article{vaswani2017attention,
  title={Attention is all you need},
  author={Vaswani, Ashish and Shazeer, Noam and others},
  journal={Advances in neural information processing systems},
  year={2017}
}
```
在內文中，使用以下指令引用：
- `\citet{vaswani2017attention}` → Vaswani et al. (2017)
- `\citep{vaswani2017attention}` → (Vaswani et al., 2017)

#### 圖、表與智慧引用

為你的圖表加上 `\label`，並使用 `\cref` 引用。
```latex
% 表格
\begin{table}[ht]
    \caption{這是一個表格}
    \label{tab:my_table}
    ...
\end{table}

% 圖片
\begin{figure}[ht]
    \includegraphics[width=0.8\textwidth]{figures/some_pic.png}
    \caption{這是一張圖}
    \label{fig:my_figure}
\end{figure}

% 內文引用
如 \cref{tab:my_table} 與 \cref{fig:my_figure} 所示...
% 輸出 -> 如 表 3.1 與 圖 3.2 所示...
```

#### 名詞縮寫 (Acronyms)

1.  **定義**：在檔案開頭處定義縮寫。
    ```latex
    \newacronym{nlp}{NLP}{Natural Language Processing}
    ```
2.  **使用**：在文章中用 `\gls{}`。
    ```latex
    % 第一次使用
    本研究專注於 \gls{nlp} ...
    % 輸出 -> 本研究專注於 Natural Language Processing (NLP) ...

    % 後續使用
    ... \gls{nlp} 的最新發展 ...
    % 輸出 -> ... NLP 的最新發展 ...
    ```
編譯後會自動在目錄後方生成一份「名詞縮寫對照表」。

#### 程式碼區塊

```latex
\begin{lstlisting}[language=Python, caption={Python 範例}]
def hello():
    print("Hello, World!")
\end{lstlisting}
```

#### 演算法/偽代碼

```latex
\begin{algorithm}[ht]
    \caption{梯度下降法}
    \label{alg:gd}
    \begin{algorithmic}[1]
        \Require 學習率 $\alpha$
        \While{尚未收斂}
            \State 更新參數 $\theta$
        \EndWhile
    \end{algorithmic}
\end{algorithm}
```

## ❓ 常見問題 (FAQ)

1.  **編譯時出現 `File not found` 錯誤？**
    -   **檢查 `\finalprintfalse`**：如果你的 `approval_page.pdf` 還沒準備好，請確保此開關為 `false`。
    -   **檢查圖片路徑**：確認 `\includegraphics` 中的檔案路徑是否正確。

2.  **參考文獻或目錄顯示 `[?]` 或不正確？**
    -   **多編譯幾次**。LaTeX 需要多次編譯來更新交叉引用。請連續編譯 **2-3 次**。

3.  **中文字變成亂碼或空白？**
    -   請確認你使用的是 **XeLaTeX** 引擎進行編譯，而不是 pdfLaTeX 或 LuaLaTeX。

4.  **如何修改字體？**
    -   在 `dasdan.tex` 中找到 `\setCJKmainfont` (中文字體) 和 `\setmainfont` (英文字體) 指令，將後方的字體名稱換成你電腦中已安裝的字體即可。

---

**最後，祝大家畢業順利，前程似錦！**