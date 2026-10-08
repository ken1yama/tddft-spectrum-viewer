# TDDFT Spectrum Viewer

[English](#english) | [日本語](#日本語)

---

## English

A browser-based tool that reads the TDDFT output (`.out` / `.log`) of Gaussian and shows the transition table and the UV-Vis spectrum, in the spirit of GaussSum. It is a single static file (`index.html`) with no dependencies and no server.

**Your files never leave your computer** – everything is processed inside the browser.

### Usage

1. Open `index.html` in a browser (or host it on any static web server, e.g. GitHub Pages).
2. Drop a Gaussian output file onto the page, or choose it with the button.
3. Adjust the spectrum and download what you need.

### Features

- **Transition table** – energy (cm⁻¹, eV), wavelength, oscillator strength, symmetry, and the major / minor orbital contributions (`H-1->LUMO (42%)` style). The major-contribution threshold is adjustable (default 10 %).
- **Calculation details** – route section, functional, basis set, solvent model, charge, multiplicity, formula, point group, number of basis functions, electrons / HOMO number, SCF and TD energies, and, when present, ZPE, enthalpy, Gibbs energy, imaginary frequencies, optimization status, termination status and elapsed time.
- **Spectrum** – Gaussian or Lorentzian band shape; x axis in nm, eV or 10³ cm⁻¹; left / right edge, FWHM (cm⁻¹ or eV), optional reversed x axis; optional y-axis maxima for ε and for the oscillator-strength bars; figure width / height and font sizes. The range is adjusted automatically every time a file is loaded.
- **Download** – transition table (CSV), spectrum figure (PNG / SVG), spectrum data (CSV).
- **Languages** – Japanese and English.
- Optimization or multi-step jobs: each block of excited states is detected and can be selected (the last block is shown by default). Open-shell (UKS) output is supported.

### Calculation notes

- Contribution (%) = 2c² × 100 for closed-shell and c² × 100 for open-shell, where c is the CI coefficient printed by Gaussian. Only excitation (`->`) amplitudes are used; de-excitation (`<-`) amplitudes are ignored, so the sum can exceed 100 % for non-TDA calculations. Gaussian prints only coefficients above its own threshold.
- Energies in cm⁻¹ are obtained from the eV values printed by Gaussian (1 eV = 8065.54 cm⁻¹) and the wavelength from the wavenumber, so they can differ slightly from the nm value printed in the output.
- Gaussian band: ε(ν̃) = Σᵢ 1.3062974×10⁸ · fᵢ / σ · exp[−((ν̃ − ν̃ᵢ)/σ)²], σ = FWHM / (2√ln 2) (cm⁻¹), in M⁻¹ cm⁻¹. The Lorentzian band uses the same integrated intensity.

### Not supported yet

- ORCA output (planned)
- Gaussian output other than TD-DFT / CIS excited states

### Tested with

Gaussian 16 TD-DFT output, closed shell (RB3LYP) and open shell (UCAM-B3LYP, doublet and triplet, `td=(full)`, SCRF, `genecp`). Frequency-job information has been checked only with synthetic data – feedback with real outputs is welcome.

### License

MIT – see [LICENSE](LICENSE).

---

## 日本語

Gaussian の TDDFT 計算の出力ファイル（`.out` / `.log`）を読み込み、GaussSum のように遷移テーブルと UV-Vis スペクトルを表示するブラウザ用ツールです。`index.html` 1 ファイルだけで動作し、サーバーや外部ライブラリは不要です。

**ファイルは外部に送信されません**。処理はすべてブラウザ内で行われます。

### 使い方

1. `index.html` をブラウザで開きます（GitHub Pages など、静的な Web サーバーに置いても動きます）。
2. Gaussian の出力ファイルをページにドロップするか、ボタンで選択します。
3. スペクトルを調整し、必要なものをダウンロードします。

### 機能

- **遷移テーブル**: エネルギー（cm⁻¹、eV）、波長、振動子強度、対称性、主要・副寄与の軌道（`H-1->LUMO (42%)` 形式）。主要寄与のしきい値は変更できます（初期値 10 %）。
- **計算の詳細**: ルート行、汎関数、基底関数、溶媒モデル、電荷、多重度、分子式、点群、基底関数の数、電子数と HOMO 番号、SCF と TD のエネルギー。あれば、ZPE、エンタルピー、ギブズエネルギー、虚振動数、最適化の収束、終了状態、経過時間も表示します。
- **スペクトル**: ガウス型またはローレンツ型。横軸は nm、eV、10³ cm⁻¹ から選択。左端・右端、FWHM（cm⁻¹ または eV）、横軸の反転、ε と振動子強度の縦軸最大値、図の幅・高さ・フォントサイズを設定できます。ファイルを読み込むたびに範囲を自動調整します。
- **ダウンロード**: 遷移テーブル（CSV）、スペクトル図（PNG / SVG）、スペクトルの数値（CSV）。
- **表示言語**: 日本語と英語。
- 構造最適化など複数ステップのジョブでは、励起状態のブロックごとに検出して選択できます（初期表示は最後のブロック）。開殻（UKS）の出力にも対応しています。

### 計算についての注意

- 寄与率（%）は、閉殻では 2c² × 100、開殻では c² × 100 です（c は Gaussian が出力する CI 係数）。励起（`->`）の成分だけを使い、脱励起（`<-`）の成分は無視します。そのため、非 TDA の計算では合計が 100 % を超えることがあります。Gaussian は、自身のしきい値以上の係数だけを出力します。
- cm⁻¹ のエネルギーは、Gaussian が出力する eV の値から求め（1 eV = 8065.54 cm⁻¹）、波長はその波数から計算します。そのため、出力ファイルに書かれた nm の値と、わずかに異なることがあります。
- ガウス型のバンドは、ε(ν̃) = Σᵢ 1.3062974×10⁸ · fᵢ / σ · exp[−((ν̃ − ν̃ᵢ)/σ)²]、σ = FWHM / (2√ln 2)（cm⁻¹）で、単位は M⁻¹ cm⁻¹ です。ローレンツ型は、同じ積分強度で計算します。

### 未対応

- ORCA の出力（対応予定）
- TD-DFT / CIS の励起状態以外の Gaussian 出力

### 動作確認

Gaussian 16 の TD-DFT 出力で、閉殻（RB3LYP）と開殻（UCAM-B3LYP、二重項・三重項、`td=(full)`、SCRF、`genecp`）を確認しています。振動計算に関する情報の表示は、人工的なデータでのみ確認しています。実際の出力でうまく動かない場合は、ぜひ教えてください。

### ライセンス

MIT。詳細は [LICENSE](LICENSE) を参照してください。
