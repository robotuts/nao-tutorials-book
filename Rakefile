namespace :book do
  # desc 'prepare build'
  # task :prebuild do
  #   Dir.mkdir 'images' unless Dir.exists? 'images'
  #   Dir.glob("book/*/images/*").each do |image|
  #     FileUtils.copy(image, "images/" + File.basename(image))
  #   end
  # end

  desc 'build basic book formats'
  # task :build => :prebuild do
  task :build do
    puts "Converting to HTML..."
    `bundle exec asciidoctor book.asc`
    puts " -- HTML output at book.html"

    puts "Converting to EPub..."
    `bundle exec asciidoctor-epub3 book.asc`
    puts " -- Epub output at book.epub"

    puts "Converting to Mobi (kf8)..."
    `bundle exec asciidoctor-epub3 -a ebook-format=kf8 book.asc`
    puts " -- Mobi output at book.mobi"

    puts "Converting to PDF... (this one takes a while)"
    `bundle exec asciidoctor-pdf book.asc 2>/dev/null`
    puts " -- PDF  output at book.pdf"
  end
end

task :default => "book:build"
