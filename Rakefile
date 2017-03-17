namespace :book do
  desc 'prepare build'
  task :prebuild do
    Dir.mkdir 'images' unless Dir.exists? 'images'
    Dir.glob("book/*/images/*").each do |image|
      FileUtils.copy(image, "images/" + File.basename(image))
    end
  end

  desc 'build basic book formats'
  task :build => :prebuild do
    puts "Converting to HTML..."
    `bundle exec asciidoctor VizWorkshop.asc -o VizWorkshop.html`
    puts " -- HTML output at VizWorkshop.html"

    puts "Converting to PDF... (this one takes a while)"
    `bundle exec asciidoctor-pdf VizWorkshop.asc -o VizWorkshop.pdf`
    puts " -- PDF  output at VizWorkshop.pdf"
  end
  
  desc 'build html book formats'
  task :build_html => :prebuild do
    puts "Converting to HTML..."
    `bundle exec asciidoctor VizWorkshop.asc -o VizWorkshop.html`
    puts " -- HTML output at VizWorkshop.html"
  end 
  
  desc 'build html with github stylesheet'
  task :build_html_gitcss => :prebuild do
      puts "Converting to HTML with github stylesheet..."
      `bundle exec asciidoctor VizWorkshop.asc -a stylesheet=github.css -a stylesdir=./stylesheets -o VizWorkshop_github_style.html`
      puts " -- HTML output at VizWorkshop_github_style.html"
  end  
  
end

task :default => "book:build"
