# Debugging Workshop

Learning goals
* Explain what a bug is
* Explain a good approach to debugging
* Follow an effective debugging process to identify a bug
* Follow an effective debugging process to fix a bug

What is a bug?
* Incomplete method / missing information it’s expecting
* Unexpected output / return value
* It’s an error in the code
* An unexpected behavior or output in the program / any deviation from expected behavior

What can we take from this definition?
* We want to have an idea of the behavior we expect from our code
* Be clear on the assumption - write it out in plain english
* Run through the code line by line

Debugging
* Tighten the loop (get as close as you can to find the exact line the bug is coming from)
* Get visibility (use p to inspect everything to help you home in on the exact line)
* Once you know the one thing that is wrong, out of place, misspelled, or not giving you what you expect, try to fix it.

Private Methods
* It's a type of method that you can ONLY call from inside the class where it's defined. This allows you to control access to your methods.

## Exercises

### Exercise 1
```
def say_hello(name)
  "hello #(name)"
end
```

```
def say_hello(name)
  "hello #{name}"
end
```

### Exercise 2
```
def encode(plaintext, key)
  cipher = key.chars.uniq + (('a'...'z').to_a - key.chars)
  ciphertext_chars = plaintext.chars.map do |char|
    (65 + cipher.find_index(char)).chr
  end
  ciphertext_chars.join
end

def decode(ciphertext, key)
  cipher = key.chars.uniq + (('a'...'z').to_a - key.chars)
  plaintext_chars = ciphertext.chars.map do |char|
    cipher[65 - char.ord]
  end
  plaintext_chars.join
end

# Intended output:
#
# > encode("theswiftfoxjumpedoverthelazydog", "secretkey")
# => "EMBAXNKEKSYOVQTBJSWBDEMBPHZGJSL"
#
# > decode("EMBAXNKEKSYOVQTBJSWBDEMBPHZGJSL", "secretkey")
# => "theswiftfoxjumpedoverthelazydog"
```

```
class Cipher

  def encode(plaintext, key)
    # key, display each chars once 
    # + all other chars of alpha which not included
    # 'secretykey'
    cipher = key.chars.uniq + (('a'..'z').to_a - key.chars)
    ciphertext_chars = plaintext.chars.map do |char|
      (65 + cipher.find_index(char)).chr
    end
    ciphertext_chars.join
  end
  # encoded_text = "EMBAXNKEKSYOVQTBJSWBDEMBPHZGJSL"
  # text = "theswiftfoxjumpedoverthelazydog"

  def decode(ciphertext, key)
    cipher = key.chars.uniq + (('a'..'z').to_a - key.chars)
    plaintext_chars = ciphertext.chars.map do |char|
      cipher[char.ord - 65]
    end
    plaintext_chars.join
  end
end
```

