# RA2111026010199_Factwise_BE
factwise selection questions

# question1 ans
  
    def number_to_words_length(n):
    
        ones = ["", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten",
            "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"]
        tens = ["", "", "twenty", "thirty", "forty", "fifty", "sixty", "seventy", "eighty", "ninety"]
        hundred = "hundred"
        thousand = "thousand"
        and_word = "and"

        total_letters = 0

        for i in range(1, n + 1):
            if i == 1000:
                total_letters += len("onethousand")
            else:
                num_letters = 0
                if i >= 100:
                    num_letters += len(ones[i // 100])
                    num_letters += len(hundred)
                    if i % 100 != 0:
                        num_letters += len(and_word)
                if i % 100 < 20:
                    num_letters += len(ones[i % 100])
                else:
                    num_letters += len(tens[(i % 100) // 10])
                    num_letters += len(ones[i % 10])
                total_letters += num_letters

        return total_letters
    
    total_letters_used = number_to_words_length(1000)
    print("Total number of letters used from 1 to 1000 inclusive:", total_letters_used)


# Question 2 ans

    def maxScore(cardPoints, k):
      n = len(cardPoints)
      if k == n:
          return sum(cardPoints)
    
      total_sum = sum(cardPoints)
      window_size = n - k
      min_subarray_sum = float('inf')
      current_subarray_sum = 0

     
      for i in range(window_size):
          current_subarray_sum += cardPoints[i]

      min_subarray_sum = current_subarray_sum

    
      for i in range(window_size, n):
          current_subarray_sum += cardPoints[i] - cardPoints[i - window_size]
          min_subarray_sum = min(min_subarray_sum, current_subarray_sum)

      return total_sum - min_subarray_sum


    def main():
      cardPoints = list(map(int, input("Enter the card points separated by spaces: ").split()))
      k = int(input("Enter the number of cards to take: "))
      print("Maximum score:", maxScore(cardPoints, k))


    if __name__ == "__main__":
      main()

