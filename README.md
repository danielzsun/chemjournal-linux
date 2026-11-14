# ChemJournal Linux

Generate editable **ChemDraw CDXML** files and SVG/PNG previews from SMILES, SDF, MOL and related structural inputs. Macrocycles use a folded drawing preference, with a verified cyclosporin A coordinate template.

## Download the complete workflow

[**Download ChemJournal Linux 0.2.1 (67 MB)**](https://github.com/danielzsun/chemjournal-linux/releases/download/v0.2.1/chemjournal-linux-0.2.1.zip)

[Release details](https://github.com/danielzsun/chemjournal-linux/releases/tag/v0.2.1) · [SHA-256 checksum](https://github.com/danielzsun/chemjournal-linux/releases/download/v0.2.1/chemjournal-linux-0.2.1.zip.sha256)

The release ZIP contains the complete Python source, installable application wheel, pinned Linux dependency wheels, launchers, freely licensed fonts, automated tests, documentation, and editable examples for cyclosporin A, daraxonrasib, elironrasib, rapamycin and everolimus.

## Install on your Linux workstation

The bundled **offline** installation targets **CPython 3.12, x86-64 Linux, glibc 2.28 or newer**. Python and its `venv`/`ensurepip` support must already be installed. The required system libraries are `libX11.so.6`, `libXext.so.6`, `libXrender.so.1`, `libexpat.so.1`, `libstdc++.so.6` and `libz.so.1`, plus the standard glibc runtime. A graphical session is not required.

```bash
curl -fLO https://github.com/danielzsun/chemjournal-linux/releases/download/v0.2.1/chemjournal-linux-0.2.1.zip
curl -fLO https://github.com/danielzsun/chemjournal-linux/releases/download/v0.2.1/chemjournal-linux-0.2.1.zip.sha256
sha256sum -c chemjournal-linux-0.2.1.zip.sha256
unzip chemjournal-linux-0.2.1.zip
cd chemjournal-linux-0.2.1
bash install.sh
```

For another CPython 3.12+ version or Linux architecture with compatible prebuilt dependencies available, use an internet connection and run `bash install.sh --online` instead. Alpine/musl Linux is outside the bundled offline target.

Setup creates a local `.venv`, checks file integrity and the native ChemDraw export capability, then exports and reimports six structures to verify their chemical identities and stereochemistry. No system Python modification or administrator access is requested by the installer.

## Generate a drawing

From the extracted workflow folder:

```bash
bash run.sh molecules.sdf -o drawings --labels name --write-sdf
bash run.sh examples/cyclosporin_a.sdf -o cyclosporin-drawing --labels name
bash run.sh examples/macrocycles/Everolimus.smi -o everolimus-drawing --labels name
bash run.sh --help
bash check.sh
```

See the README inside the ZIP for all supported formats, style settings, system prerequisites and usage examples. Use a fresh output directory for each conversion. The generated `report.json` records chemical checks and review flags.

## Verification and limits

The installed application wheel passed **67 automated tests** and six structure checks on the development **Windows** host. A Linux runtime was unavailable there; Linux native execution is verified by the included installation checks on the destination workstation. The ZIP includes a detailed release-validation record and per-file hashes.

Previews are rendered by RDKit. Native ChemDraw visual rendering remains unverified, and final publication appearance should be reviewed in ChemDraw. Output is editable CDXML; use ChemDraw's Save As command if binary CDX is required.

Third-party license notices, including the SIL Open Font License for the bundled Liberation Sans fonts, are included in the ZIP.
