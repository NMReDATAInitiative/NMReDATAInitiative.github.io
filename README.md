# The Slate theme

[![Build Status](https://travis-ci.org/pages-themes/slate.svg?branch=master)](https://travis-ci.org/pages-themes/slate) [![Gem Version](https://badge.fury.io/rb/jekyll-theme-slate.svg)](https://badge.fury.io/rb/jekyll-theme-slate)

*Slate is a Jekyll theme for GitHub Pages. You can [preview the theme to see what it looks like](http://pages-themes.github.io/slate), or even [use it today](#usage).*

![Thumbnail of Slate](thumbnail.png)

## Usage

To use the Slate theme:

1. Add the following to your site's `_config.yml`:

    ```yml
    theme: jekyll-theme-slate
    ```

2. Optionally, if you'd like to preview your site on your computer, add the following to your site's `Gemfile`:

    ```ruby
    gem "github-pages", group: :jekyll_plugins
    ```

## Customizing

### Configuration variables

Slate will respect the following variables, if set in your site's `_config.yml`:

```yml
title: [The title of your site]
description: [A short description of your site's purpose]
```

Additionally, you may choose to set the following optional variables:

```yml
show_downloads: ["true" or "false" to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
```

### Stylesheet

If you'd like to add your own custom styles:

1. Create a file called `/assets/css/style.scss` in your site
2. Add the following content to the top of the file, exactly as shown:
    ```scss
    ---
    ---

    @import "{{ site.theme }}";
    ```
3. Add any custom CSS (or Sass, including imports) you'd like immediately after the `@import` line

*Note: If you'd like to change the theme's Sass variables, you must set new values before the `@import` line in your stylesheet.*

### Layouts

If you'd like to change the theme's HTML layout:

1. [Copy the original template](https://github.com/pages-themes/slate/blob/master/_layouts/default.html) from the theme's repository<br />(*Pro-tip: click "raw" to make copying easier*)
2. Create a file called `/_layouts/default.html` in your site
3. Paste the default layout content copied in the first step
4. Customize the layout as you'd like

### Overriding GitHub-generated URLs

Templates often rely on URLs supplied by GitHub such as links to your repository or links to download your project. If you'd like to override one or more default URLs:

1. Look at [the template source](https://github.com/pages-themes/slate/blob/master/_layouts/default.html) to determine the name of the variable. It will be in the form of `{{ site.github.zip_url }}`.
2. Specify the URL that you'd like the template to use in your site's `_config.yml`. For example, if the variable was `site.github.url`, you'd add the following:
    ```yml
    github:
      zip_url: http://example.com/download.zip
      another_url: another value
    ```
3. When your site is built, Jekyll will use the URL you specified, rather than the default one provided by GitHub.

*Note: You must remove the `site.` prefix, and each variable name (after the `github.`) should be indent with two space below `github:`.*

For more information, see [the Jekyll variables documentation](https://jekyllrb.com/docs/variables/).

## Roadmap

See the [open issues](https://github.com/pages-themes/slate/issues) for a list of proposed features (and known issues).

## Project philosophy

The Slate theme is intended to make it quick and easy for GitHub Pages users to create their first (or 100th) website. The theme should meet the vast majority of users' needs out of the box, erring on the side of simplicity rather than flexibility, and provide users the opportunity to opt-in to additional complexity if they have specific needs or wish to further customize their experience (such as adding custom CSS or modifying the default layout). It should also look great, but that goes without saying.

## Contributing

Interested in contributing to Slate? We'd love your help. Slate is an open source project, built one contribution at a time by users like you. See [the CONTRIBUTING file](docs/CONTRIBUTING.md) for instructions on how to contribute.

### Previewing the theme locally

If you'd like to preview the theme locally (for example, in the process of proposing a change):

1. Clone down the theme's repository (`git clone https://github.com/pages-themes/slate`)
2. `cd` into the theme's directory
3. Run `script/bootstrap` to install the necessary dependencies
4. Run `bundle exec jekyll serve` to start the preview server
5. Visit [`localhost:4000`](http://localhost:4000) in your browser to preview the theme

### Running tests

The theme contains a minimal test suite, to ensure a site with the theme would build successfully. To run the tests, simply run `script/cibuild`. You'll need to run `script/bootstrap` one before the test script will work.



## [NMReDATA initiative](https://nmredata.org/)

_generate, store and share the data extracted from set of NMR spectra associated to a compound_  

- [Home](https://nmredata.org/)
- / Who are we?
- [/ The Format](https://nmredata.org/format.html)
- [/ In the news ...](https://nmredata.org/timeline.html)

### /  Who are we?

      The NMReDATA Initiative is coordinated by [Damien Jeannerat (University of Geneva, Swizerland)](https://www.unige.ch/sciences/chiorg/jeannerat/) since 2016. 

      The main communication medium is a mailing list,
 and SLACK channels are used to exchange on specific topics. The 
partners of the Initiative are listed below. They showed interest in the
 NMReDATA Initiative and are susceptible to provide advice on the 
development of the format or related aspects such as database structure,
 etc. We also have a mailing list of “followers” of the Initiative but 
are not listed below.

         **Individual members**

       **Damien Jeannerat**, [University of Geneva](https://www.unige.ch/sciences/chiorg/jeannerat/), Switzerland

 
  Interest in data processing and methodology developments in 
small-molecule NMR. Focus on providing simplified very high resolution 
2D spectra to facilitate automatic extraction of NMR 
data. Coordinator of the NMReDATA Initiative. 

         **Julien Wist**, University of Valle, Colombia    

 
  Graduated from the University of Lausanne, Switzerland. Obtained his 
Ph.D at Geoffrey Bodenhausen's Lab at Ecole Polytechnique Fédérale de 
Lausanne, Switzerland working on slow dynamics in proteins. Joined the 
Universidad Nacional de Colombia in Bogotá in 2006 and started there to 
build an NMR community. Moved to Universidad del Valle in Cali, Colombia
 in 2010 and works on cheminformatics (www.cheminfo.org) and NMR to help
 extracting information from complex mixtures. Member of the associate 
board of _Magnetic Resonance in Chemistry_.  

        **Jean-Marc Nuzillard**, Université de Reims-Champagne-Ardenne and Centre National de la Recherche Scientifique, France

   Leader of the[ "Isolement et Structure" research group](http://eos.univ-reims.fr/LSD/ISgroup.html) at the Institut de Chimie Moléculaire de Reims. Developer of [LSD](http://www.univ-reims.fr/LSD/JmnSoft/),
 a Computer-Assisted Structure Elucidation software. Over 160 
publications in the fields of natural product chemistry and NMR data 
acquisition, processing and interpretation.

        **Nils Schloerer**,[IDNMR](http://www.idnmr.uni-koeln.de/15115.html?&L=1) and University of Cologne, Germany

   NMR
 facility manager at the Department of Chemistry, University of Cologne.
 Interested in modern and affordable technologies for academic NMR labs 
(e.g. fast NMR methods and their application to ‘routine’ NMR) as well 
as in electronic data and laboratory management. Trying to find ways how
 to teach chemists to ‘read’ and handle NMR data in an adequate fashion.

        **Stefan Kuhn**, [IDNMR](http://www.idnmr.uni-koeln.de/15115.html?&L=1) and De Montfort University, Leicester, United Kingdom

   Working on software and standards in chemoinformatics and NMR. Involved in various projects including _nmrshiftdb2_ and _Chemistry Development Kit_. Interested in establishing standards for handling and long-term storage of analytical data.

        **Mate Erdelyi**, Department of Chemistry - BMC, University of Uppsala, Sweden

   Professor
 in organic chemistry with interest in NMR spectroscopy, medicinal 
chemistry, natural product chemistry and physical organic chemistry. 
Graduated at Semmelweis University, Hungary, (1999) obtained Ph.D. in 
organic chemistry at Uppsala University, Sweden (2004), following three 
postdoc projects initiated independent research at the University of 
Gothenburg (2008) and more recently at the University of Uppsala (2017).

        **Pavel Kessler**, Bruker

        **Fabrice Moriaud**, Bruker

        **Manuel Perez**, Mestrelab

  PhD
 studies at University of Liverpool with Proffesor Ray Abraham on “NMR 
prediction of Amides and Peptides” and development of the CHARGE NMR 
prediction software. Worked
 for Pfizer in the UK in the areas of NMR, Comp Chemistry and PK/PD 
departments. Internal Awards: Global prize, runner-up Best Medicinal 
Chemist in 2009. Since 2011, Senior Vice President – Strategy and 
Business Development EMEA at Mestrelab Research. Member of the Associate
 Editorial Board at MRC. Published in many different areas: Parallel 
Synthesis, Synthetic Method Development, NMR, Computational Chemistry 
and Medicinal Chemistry and is inventor in three patents in the Pain 
Therapeutic Area.

        **Adolfo Botana**, Jeol

        **[Christoph Steinbeck](http://cheminf.uni-jena.de/)**, University of Jena, Germany

 
  Professor for Analytical Chemistry, Cheminformatics and Chemometrics 
at the Friedrich-Schiller-University in Jena, Germany. Was founding 
editor-in-chief of the Journal of Cheminformatics, director of the 
Metabolomics Society, chairman of the Computers-Information-Chemistry 
(CIC) division of the German Chemical Society. Founder of [Chemistry Development Kit](http://cdk.github.io/). Developed structure elucidation softwares Lucy and SENECA.

        **Mikhail Elyashberg**, Moscow Department of Advanced Chemistry Development Ltd. (ACD/Labs), Canada-Russia

 
  Mikhail Elyashberg graduated from the Faculty of Physics at the Tomsk 
University (1959), Russia. Professor, Ph.D. (in Phys.-Math.), Dr. habil.
 (in Chem.). Untill 2001,  head of Laboratory of molecular spectroscopy 
(NMR, HRMS, FTIR, Raman, UV-VIS) at All-Russian Institute of Organic 
Synthesis, Moscow. Since 2001, senior scientist at Moscow Department of 
ACD/Labs and a leading researcher at Vernadsky Institute of Russian 
Academy of Science, Moscow.  One of the leading developers of a CASE 
expert system ACD/Structure Elucidator.

        **Dimitris Argyropoulos**, ACD/Labs

        **Antony Williams, **National Center for Computational Toxicology, US Environmental Protection Agency, USA

   Analytical
 scientist specializing in NMR and later in cheminformatic. Graduated 
from Liverpool University, UK (BSc. Hons. Chemistry) and the University 
of London, UK (PhD Chemistry). NMR Technology Leader at Eastman-Kodak 
for over 5 years before joining ACD/Labs as their NMR Software Product 
Manager and leaving the company 10 years later as their Chief Science 
Officer. While at ACD/Lab, worked on analytical data processing, NMR 
prediction and computer-assisted structure elucidation. He was a founder
 of the ChemSpider website that was acquired by the Royal Society of 
Chemistry and now hosts over 50,000 users a day. One of his specific 
interests was the sharing of spectral data from the site. Involved with 
the development of the [Spectral Game](https://jcheminf.springeropen.com/articles/10.1186/1758-2946-1-9). Published over 160 peer-reviewed publications &gt;25 book chapters and 6 books, many of these [NMR related](http://www.chemconnector.com/publications/).

        **Bozhana Mikhova, **Bulgarian Academy of Sciences, Bulgaria

   Associate
 Professor at the Institute of Organic Chemistry with Centre of 
Phytochemistry with research interests in the field of small molecule 
NMR - natural products and synthetic derivatives with potential 
biological activity. Participated in projects about NMR spectral data 
collections with ISISBase and SciDex. Member of the _Editorial Board_ of _Magnetic Resonance in Chemistry_ responsible mainly for the papers in section _Letter – spectral assignment_.

        **Craig Butts, **University of Bristol, United Kingdom

   Professor
 of Structural and Mechanistic Chemistry, specialising in the 
development and application of small molecule NMR spectroscopy with 
particular interest in the study of 3-dimensional structure using 
accurate and quantitative NMR methods. Director of Chemical NMR 
Facilities, responsible for the collection and curation of hundreds of 
thousands of NMR datasets annually.

[![Image](https://nmredata.org/_Media/csearch_logo_med.png)](http://nmrpredict.orc.univie.ac.at/)

        **Wolfgang Robien, **University of Wien, Austria

   Associate Professor at University of Vienna, author of the 

“[CSEARCH"](http://nmrpredict.orc.univie.ac.at/) NMR-database.
 CSEARCH-technology and/or data are already implemented into 
variousother pieces of software. He is cooperating with Biorad, Bruker, 
Chemical Abstracts Service, Mestrelab, Modgraph and Wiley.

        **Tomas Lebl, **University of St Andrews, UK

 
  Manager of the liquid-state NMR facility at the University of St 
Andrews since 2004. Managing the walk-up automated NMR service provided 
by 6 fully automated [NMR spectrometers](http://nmr.st-andrews.ac.uk),
 collaborates as NMR expert on various research projects across the 
chemical and biological sciences. Co-author of 64 publications (H-index 
18, WOS). Expertise in conformational analysis of small molecules, RDC 
analysis, reaction monitoring, diffusion ordered spectroscopy, etc. 
Interest in data management of high throughput NMR laboratories and 
driving force behind the [NOMAD project](http://nomad.wp.st-andrews.ac.uk).

        **Gregory M. Banik**, Bio-Rad Laboratories, Informatics Division 

   General
 Manager of the Informatics Division of Bio-Rad Laboratories and creator
 of its award-winning KnowItAll software for analytical chemistry, 
overseeing the Division’s Bio-Rad Sadtler spectral databases of NMR, IR,
 Raman, UV-Vis, and mass spectra and SpectraBase cloud-based spectral 
repository.  Received a B.A. degree in Chemistry and Computer Science 
from Grinnell College and M.S. and Ph.D. degrees in organic chemistry 
from Northwestern University. Previously held management positions at 
Molecular Simulations Inc. (MSI, now part of BIOVIA/Dassault Systèmes), 
UMI (now ProQuest), Thomson Reuter's Institute for Scientific 
Information (ISI, now Clarivate Analytics), and Abbott Laboratories 
Pharmaceutical Products Division (now AbbVie) as well as a lectureship 
position at Northwestern University.  A member of the IUPAC Subcommittee
 on Cheminformatics Data Standards (SCDS), member of the Data Interest 
Group/Chemistry (DIGChem) and chair of its NMR/spectral repository 
working group, member of the NMReDATA initiative, member of the Society 
of Applied Spectroscopy, member of the Coblentz Society, member of the 
Vidocq Society, member of the American Chemical Society, and former 
Chair of the American Chemical Society Division of Chemical Information 
(CINF).

**     Software developers**

             **nmreshiftdb2**, [www.nmrshiftdb.org](http://www.nmrshiftdb.org/)

   Nmrshiftdb2
 is an open-data repository for organic structures and their nuclear 
magnetic resonance spectra. It allows for spectrum prediction (

13C, 

1H
 and other nuclei) as well as for searching spectra, structures and 
other properties. nmrshiftdb2 can import and export NMReDATA.  

             **Cheminfo**, [www.cheminfo.org](http://www.cheminfo.org/)

   Open source (MIT license) project developed mainly by Luc Patiny (Ecole
 Polytéchnique Fédérale de Lausanne, Lausanne, Switzerland) and Julien 
Wist, (Universidad del Valle en Cali, Colombia). The aim of this project
 is to bring efficient, research-grade, cheminformatics tools into the 
browser, thus is written exclusively in javaScript that is natively 
supported by all browsers. This technology was chosen because it allows 
to develop tools that can run either on the server or on the client and 
because it enable the user to access all the power of the system without
 installing a single package. It will run on all operating systems and 
is suitable for mobile devices. Cheminfo.org
 permits to perform complex operations on many different kind of 
chemical data, such as molecules and spectra, but also includes 
efficient libraries to work with images (microscopy, petri dishes, 
etc.). Cheminfo.org showcases the potential of this paradigm shift, from
 the standard c++ libraries and standalone desktop application to the 
all in browser. Many demo tools can be found that can inspire others to 
contribute to the effort.  

          ** Bio-Rad Laboratories**, Informatic Division, 

[www.knowitall.com](http://www.knowitall.com/)

   Bio-Rad
 is a world leader in spectral databases and spectroscopy software. 
Bio-Rad’s Informatics Division, founded as Sadtler Research Laboratories
 in Philadelphia in 1874, has the longest history of any spectral 
database producer. Sadtler created the spectral reference industry in 
the 1950’s with its print library collections, and after being acquired 
by Bio-Rad in 1978, launched the first commercial spectral database 
system for personal computers just two years later. With its 
award-winning KnowItAll® software and database product line for 
Microsoft Windows and its SpectraBase™ product line for the web, the 
Informatics Division has been at the forefront of innovative spectral 
database and search technology and has amassed the world’s largest 
collection of spectral reference databases, with over 2.4 million 
spectra and counting. Bio-Rad is exploring ways to incorporate the 
NMReDATA format in future versions of its products.

             **NOMAD**, 

[nomad.wp.st-andrews.ac.uk](http://nomad.wp.st-andrews.ac.uk)![Image](https://nmredata.org/_Media/nomad---logo-2_med.png)

   A
 research data management system that provides fast and secure access to
 NMR data. NOMAD automatically captures and stores data generated by NMR
 instruments and provides seamless tools for annotating, sharing and 
editing the data. Furthermore, NOMAD offers a centralised dashboard for 
management of 24/7 operating open access scientific laboratories. It has
 developed over last five years as collaborative project between School 
of Chemistry and Computer Science. The prototype of the system is 
implemented in the NMR facility at the University of St Andrews, 
collating data from 6 NMR instruments, with a user base of around 600 
researchers and students from about 35 research groups. One of the 
current primary objectives of the team is to form a spin-off company 
 that would allow sharing NOMAD system and NMR data with other NMR labs .
 The NMReDATA platform seems to fit that purpose very well.

![Image](https://nmredata.org/_Media/acdlabs_logo_med.png)

             **ACD/Labs**,[www.acdlabs.com](http://www.acdlabs.com)

 
  ACD/Labs has over two decades of experience boosting the productivity 
of synthetic and analytical chemistry laboratories worldwide with unique
 software capabilities to understand and preserve the relationship 
between chemistry projects and analytical data. ACD/NMR Workbook Suite 
provides advanced processing and interpretation tools for NMR 
spectroscopists looking to deliver fast turnarounds on 
proof-of-structure reports. As part of the ACD/Spectrus Platform, the 
software radically simplifies workflows and makes the reporting process 
faster than ever before. ACD/Spectrus Processor can already export .sdf 
files with spectra information and in the next release, targeted for 
December 2017, the **full NMReDATA format will be supported**.

![Image](https://nmredata.org/_Media/mestrelab_med.jpeg)

        **Mestrelab Research SL **[http://www.mestrelab.com](http://www.mestrelab.com/)

 
  Mestrelab Research SL is a Spanish company specialized in the 
development of state of the art software applications for handling of 
analytical chemistry data (NMR, LC/GC/MS). Mestrelab Research SL 
develops and commercializes Mnova, a World leading integrated software 
package for processing and advanced analysis of NMR and LC/GC/MS data 
with multivendor support, Phys Chem predictions and an extensive 
Worldwide user base. The company’s mission is to develop software 
solutions which become the universal processing and analysis interface 
between analytical instrumentation and chemists. **Mestrelab will explore best ways to generate the NMReDATA format in future versions of Mnova**.

            **Bruker**

   Bruker’s CMC-se software will generate .sdf including **NMReDATA by the end of 2017**.

           

**     Academic ****institutions**

        **IUPAC**

   Invitation to the IUPAC/CODATA symposium

        **DLCM**

   Poster presentation at the DLCM symposium

**     Journals**

 **Magnetic Resonance in Chemistry**, Wiley, UK

   Following the proposition by the _Associate board_, the _Editor in Chief_ decided to request electronic NMR data and spectra for all _structure paper_ submitted after 2017. Involved in the initiative: 

![Image](https://nmredata.org/_Media/mrc_logo-2_med.jpeg)

     **Patrick Giraudeau** (head of the Associate editorial board), CEISAM, University of Nates, France

     **Roberto Gil** (co-editor in chief), Carnegie Mellon University, USA

     **Gary Martin** (co-editor in chief), Merck and co., USA

     **Paul Trevorrow** (executive journal editor), Wiley, Chichester, UK

[**Contact: **Damien Jeannerat (coordinator)](mailto:damien.jeannerat@nmredata.org?subject=Interest%20of%20the%20NMReDATA%20initiative) to join the initiative!

Managed by D. Jeannerat, NMRprocess.ch
