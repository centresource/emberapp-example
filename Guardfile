# A sample Guardfile
# More info at https://github.com/guard/guard#readme
require 'guard/guard'

module ::Guard
  class BuildGuard < ::Guard::Guard
    def run_all
      puts `#{File.dirname(__FILE__)}/bin/build #{File.dirname(__FILE__)}/src/sass/screen.scss #{File.dirname(__FILE__)}/src/coffee/app.js.coffee`
    end

    def run_on_changes(paths)
      if paths.any? { |path| path =~ /\.(js|hbs|coffee)$/ }
        puts `#{File.dirname(__FILE__)}/bin/build src/coffee/app.js.coffee`
      end
      if paths.any? { |path| path =~ /\.(scss|sass)$/ }
        puts `#{File.dirname(__FILE__)}/bin/build src/sass/screen.scss`
      end
    end
  end

  class JasmineGuard < ::Guard::Guard
    def run_all
      puts `#{File.dirname(__FILE__)}/bin/build -I spec/javascripts -o spec/javascripts/build spec/javascripts/helpers/**/*.js.coffee spec/javascripts/**/*Spec.js.coffee`
    end

    def run_on_changes(paths)
      puts `#{File.dirname(__FILE__)}/bin/build -I spec/javascripts -o spec/javascripts/build #{paths.join(" ")}`
    end
  end

  class TemplateGuard < ::Guard::Guard
    def run_all
      puts `ember-precompile -f assets/templates.js #{Dir["src/templates/**/*.handlebars"].join(" ")}`
    end

    def run_on_changes(paths)
      puts `ember-precompile -f assets/templates.js #{Dir["src/templates/**/*.handlebars"].join(" ")}`
    end
  end
end

guard :build_guard do
  watch(/^src\/.*\.(js|coffee|sass|scss)$/)
end

guard :template_guard do
  watch(/^src\/.*\.handlebars$/)
end

guard :jasmine_guard do
  watch(/^spec\/.*\.coffee$/)
end
