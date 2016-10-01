require 'guard/guard'

module ::Guard
  class Less < ::Guard::Guard
    def initialize(watchers = [], options = {})
      @options = {
        :notifications => true
      }.merge options
      super(watchers, @options)
    end

    def run_on_changes(paths)
      paths.each do |file|
        output_file = file.gsub(/^(.*)\.less$/, '\1.css')
        %x(lessc "#{file}" "#{output_file}")
        message = "Successfully compiled less to css!\n"
        message += "# #{file} -> #{output_file}"#.gsub("#{Bundler.root.to_s}/", '')
        ::Guard::UI.info message
      end
    end
  end
end

guard 'haml', :run_at_start => true do
  # watch(/^.+(\.haml)/)
  watch('index.haml')
end

guard 'less', :run_at_start => true do
  watch('css/custom.less')
end