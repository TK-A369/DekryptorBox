def crypt(character, code, start_character = 'a')
  return character unless ('a'..'z').include? character
  start_number = start_character.ord
  number = character.ord - start_number + code
  number %= 26
  number += start_number
  number.chr
end

def list_of_one_letter_words(input)
  input.split(/[^\w]/).keep_if{|word| word.size==1}
end

filename = ARGV.first

fileI = File.open(filename, "r")
textI = fileI.read
fileI.close

textO = textI.downcase
#textO = textO.split(" ").join(";")
words = textO.split(/[^\w]/)
words.delete_if {|word| word.empty?}

one_letter = []
two_letters = []

ONE_LETTERS = %w(a i o u w z)

#curr_word = ""
#textO.each_char do |character|
#  if ('a'..'z').include? character then
#    curr_word = curr_word + character
#  else
#    words << curr_word
#    curr_word = ""
#  end
#end

#if curr_word != ''
#  words << curr_word
#  curr_word = ""
#end

words.each do |word|
  one_letter << word if word.size == 1
  two_letters << word if word.size == 2
  puts "Slowo \"#{word}\" ma #{word.length} liter."
end

one_letter.uniq!
two_letters.uniq!

#p one_letter
#p two_letters

#one_letter.each do |one_let|
#  ONE_LETTERS.each do |possible_letter|
#    potential = textO.gsub(one_let, possible_letter)
#    puts potential
#  end
#end

result = []
(1..26).each do |code|
  result[code] = ""
  textO.each_char do |character|
    result[code] << crypt(character, code)
  end
end

potentials = []

result.each do |input|
  next if input.nil?
  one_letter_words = list_of_one_letter_words(input)
  one_letter_words -= ONE_LETTERS
  puts input if one_letter_words.empty?
  potentials << input if one_letter_words.empty?
end

textO = potentials.join("\n\n")

fileO = File.open("output.txt", "w")
fileO.puts(textO)
fileO.close

#puts text
