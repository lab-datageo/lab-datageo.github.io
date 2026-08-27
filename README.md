# lab-datageo.github.io

Website resmi **Lab Data dan Komputasi Geoteknik**, Fakultas Teknik Sipil dan Lingkungan, Institut Teknologi Bandung.

Technologies this website uses:

    Jekyll
    GitHub Pages
    Twitter Bootstrap 4.4.1

Before pushing changes, please check that they will work on your system first with the plugins included in the Gemfile using the bundler tool (results served at [localhost:4000](http://localhost:4000)):

    gem install bundler
    bundle install
    bundle exec jekyll serve

To create a conda environment to locally test and host, the following should suffice:

    conda create -n jekyll -c conda-forge rb-jekyll
    conda activate jekyll
    bundle install
    bundle exec jekyll serve

## Menambah konten

Setiap koleksi (`_members/`, `_publications/`, `_projects/`, `_funded_projects/`, `_student_research/`, `_research_themes/`) punya `_template.md` berisi field front-matter yang diperlukan. Salin template tersebut untuk membuat entri baru.
