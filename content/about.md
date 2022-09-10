---
title: How is this site made?
---

<div class="grix xs1 md1 lg3 gutter-xs7 vstretch">
    <div class="card shadow-1 rounded-3 white post-entry">
        <div class="card-image">
            <img src="/images/obsidian.png" style="max-width:200px; margin-left:auto; margin-right:auto;" alt="obsidian_logo" />
        </div>
        <div class="card-header divider">Obsidian</div>
        <div class="card-content">
            Obsidian is the tool I use to write my notes (in Markdown). Obsidian allows me, thanks to its embedded notes
            function, to cut my notes into small pieces that I then integrate into several notes.
        </div>
        <a class="entry-link" href="https://obsidian.md/" target="_blank" rel="noopener"></a>
    </div>
    <div class="card shadow-1 rounded-3 white post-entry">
        <div class="card-image">
            <img src="/images/obsidian.png" style="max-width:200px; margin-left:auto; margin-right:auto;" alt="obsidian_logo" />
        </div>
        <div class="card-header divider">Obsidian Export</div>
        <div class="card-content">
            Obsidian Export allows me to export my Obsidian Markdown notes into CommonMark format. This is a mandatory
            step because Hugo does not completely support Obsidian Markdown syntax.
        </div>
        <a class="entry-link" href="https://github.com/zoni/obsidian-export" target="_blank" rel="noopener"></a>
    </div>
    <div class="card shadow-1 rounded-3 white post-entry">
        <div class="card-image">
            <img src="/images/hugo.png" style="max-width:200px; margin-left:auto; margin-right:auto;" alt="hugo_logo" />
        </div>
        <div class="card-header divider">Hugo</div>
        <div class="card-content">
            Hugo is a static website generator. It allows me to generate a website directly from my notes (after
            converting them with Obsidian Export).
        </div>
        <a class="entry-link" href="https://gohugo.io/" target="_blank" rel="noopener"></a>
    </div>
    <div class="card shadow-1 rounded-3 white post-entry">
        <div class="card-image">
            <img src="/images/hugo.png" style="max-width:200px; margin-left:auto; margin-right:auto;" alt="hugo_logo" />
        </div>
        <div class="card-header divider">PaperMod Theme</div>
        <div class="card-content">
            PaperMod is the Hugo theme I use for my website. This theme manages the aesthetic part of the content
            (central part of the website) as well as the navbar and the theme management (light and dark).
        </div>
        <a class="entry-link" href="https://github.com/adityatelange/hugo-PaperMod" target="_blank" rel="noopener"></a>
    </div>
    <div class="card shadow-1 rounded-3 white post-entry">
        <div class="card-image">
            <img src="/images/axentix.png" style="max-width:200px; margin-left:auto; margin-right:auto;" alt="axentix_logo" />
        </div>
        <div class="card-header divider">Axentix</div>
        <div class="card-content">
            Axentix is an awesome frontend framework made by a friend of mine (by the
            way, thank you Stallos for the help). I used Axentix to add the sidenav to the left and the amazing scrollspy to the right <3. 
        </div>
        <a class="entry-link" href="https://useaxentix.com/" target="_blank" rel="noopener"></a>
    </div>
    <div class="card shadow-1 rounded-3 white post-entry">
        <div class="card-image">
            <img src="/images/github.png" style="max-width:200px; margin-left:auto; margin-right:auto;" alt="github_logo" />
        </div>
        <div class="card-header divider">Github Pages</div>
        <div class="card-content">
            Github Pages is the place where the website is hosted. I set up a GitHub Action on my repository which builds (with Hugo) and then deploys the website as soon as there is a new commit. 
        </div>
        <a class="entry-link" href="https://pages.github.com/" target="_blank" rel="noopener"></a>
    </div>
</div>