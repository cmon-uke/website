---
title: Publications

# Listing view
view: citation

# Optional banner image (relative to `assets/media/` folder).
banner:
  caption: ''
  image: ''
---
<script>
  // list current lab members to filter the publications from a specific author
  // These names will only appear in the dropdown menu if a publication exists with 
  // that name as an author. Note that author names must be consistent to be detected; 
  // no surprise middle initials or full first names 
  const authorsList = [
    "C. Becchio", "G. Borghini", "N. C. Foster", "M. Memeo", "O. Pansardi", "K. Pullar",
    "E. Scaliti", "L. Schmitz", "J. W. A. Strachan", "R. Villa", "Q. Zhao"
  ]

</script>
<script type="text/javascript" src="bibtex_js.js"></script>
<bibtex src="bibliography.bib"></bibtex>

<div id="bibfilters" class="search_bar">
  <select class="bibtex_search bibtex_generate_author" search="author">
    <option value="">Filter by Author</option>
  </select>
  <select class="bibtex_search bibtex_generate_year" search="year" id="year_filter" bibtex_sort_options="numeric: true, descending: true">
    <option value="">Filter by Year</option>
  </select>
  <input type="text" class="bibtex_search bibtex_search_textentry" id="searchbar" placeholder="Search publications">
</div>

<div class="bibtex_template">
  <b><span class="title"></span></b>
  <span class="year" style="display: none;"></span><br/>
  <span class="second_line">
    <i><span class="author" max="100"></span></i>
    <u><span class="journal"></span></u>
    <u><span class="booktitle"></span></u>
    <span class="if volume">
      <span class="volume"></span></span> 
    <span class="if number">
      (<span class="number"></span>)</span> 
    <span class="if pages">
      <span class="pages"></span></span>
  <span class="if url">
    <a class="url" target="_blank">[Link]</a>
  </span>
  <span class="if !url" >
    <span class="if doi">
    <a class="bibtexVar" href="http://dx.doi.org/+DOI+" extra="doi" target="_blank">[Link]</a></span>
  </span></span> 
</div>

<script>
function generateBibliographyHTML(startYear, endYear) {
    for (let year = endYear; year >= startYear; year--) {
      const container = document.createElement('div')
      container.classList.add('year_container')
      container.id = "year_container_"+year

        const head = document.createElement('h4')
        head.id = "bibtex_header_" + year
        head.textContent = year
        const pubs = document.createElement('div')
        pubs.classList.add("bibtex_display")
        pubs.id = "bibtex_display_" + year
        pubs.setAttribute('year',year)

        container.appendChild(head)
        container.appendChild(pubs)

        wrapper = document.getElementsByClassName('universal-wrapper')[1]
        wrapper.appendChild(container)
    }
}

// generate the bibliographies, starting from whichever year you want
generateBibliographyHTML(2003, 2025);

</script>
