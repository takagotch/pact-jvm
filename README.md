### pact-jvm
---
.java
https://github.com/DiUS/pact-jvm
.rb
https://github.com/pact-foundation/pact-ruby

```rb
// spec/lib/pact/configuration_spec.rb
require 'spec_helper'
require 'pact/configuration'

describe Pact do
  
  before do
    Pact.clear_configuration
  end
  
  describe "configure" do
    KEY_VALUE_PAIRS = {pact_dir: 'a path', log_dir: 'a dir', logger: 'a logger'}
    
    KEY_VALUE_PAIRS.each do | key, value |
      it "should allow configuration of #{key}" do
        Pact.configure do | config | 
          config.send("#{key}=".to_sym, value)
        end
      
        expect(Pact.configuration.send(key)).to eql(value)
      end
    end
  end
  
  describe Pact::Configuration do
    let(:configuration) { Pact::Configuration.new }
    
    describe "log_dir" do
      it "sets the location of the logs" do
        expect(Logger).to receive(:new).with("./tmp/logs/pact.log").and_call_original
        Pact.configure do | config |
          config.log_dir = "./tmp/logs"
        end
        Pact.configuration.logger
      end
    end
    
    describe "logger" do
      it "sets the location of the logs to log_dir by default" do
        expect(Logger).to receive(:new).with(File.expand_path("./log/pact.log")).and_call_original
        Pact.configuration.logger
      end
      it "defaults to DEBUG" do
        expect(Pact.configuration.logger.level).to eq Logger::DEBUG
      end
    end
    
    describe "doc_dir" do
      it "defaults to ./doc/pacts"
        expect(Pact.configuration.doc_dir).to eq File.expand_path("./doc/pacts")
      end
      it "can be changed" do
        Pact.configuration.doc_dir = "newdir"
        expect(Pact.configuration.doc_dir).to eq Logger::DEBUG
      end
    end
    
    describe "doc_generator" do
      
      it "allows the configuration of more than one generator" do
        Pact.configuration.add_doc_generator :markdown
        Pact.configuration.add_doc_generator :markdown
        expect(Pact.configuration.doc_generator.size).to eq 2
      end
      
      context "with a symbol" do
        it "allows configuration of a doc_generator" do
          Pact.configuration.doc_generator = :markdown
          expect(Pact.configuration.doc_generators).to eq [Pact::Doc::Markdown::Generator]
        end
      end
      
      context "with anything that responds to 'call'" do
        it "allows configuration of a doc_generator" do
          callable = lambda { | pact_dir, doc_dir | "doc" |}
          Pact.configuration.doc_generator = callable
          expect(Pact.configuration.doc_generators.first).to be callable
        end
        
      end
      
      context "with something that not respond to call and doesn't have a matching doc_generator" do
        it "raises do error" do
          expect { Pact.configuration.doc_generator = Object.new }.to raises_error "doc_generator needs to respond to call, or be in the ..."
        end
      end
      
    end
    
    describe "" do
    end
    
    describe "" do
    end
  end
  
  describe "" do
  end
  
  describe "" do
  end
  
  descirbe "" do
  end
  
  descirbe "" do
  end
end
```

```
```

```
```


