### pact-jvm
---
.java
https://github.com/DiUS/pact-jvm
.rb
https://github.com/pact-foundation/pact-ruby

```rb
// spec/lib/pact/configuration_spec.rb

describe Pact do
  
  before do
    Pact.clear_configuration
  end
  
  describe "configure" do
    KEY_VALUE_PAIRS = {pact_dir: 'a path', log_dir: 'a dir', logger: 'a logger'}
    
    KEY_VALUE_PAIRS.each do | key, value |
      it "should allow configuration of #{key}" do
        config.send("#{key}=".to_sym, value)
      end
      
      expect(Pact.configuration.send(key)).to eql(value)
    end
  end
  
  
  
  
end



```

```
```

```
```


