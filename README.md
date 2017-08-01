# step 0: compare remove duplicate strings. (done!)
# step 1: compare string #(i) with all strings.
# step 2: if 3 or more characters ANYWHERE in the string are a perfect match with another string (compared string, or CSTRING)--
# step 3: compare the rest of the previous and following characters after the match in the ISTRING  with the rest of the characters in the CSTRING.
# step 3 cont:  if they DO NOT  match, skip the CSTRING and move onto the next one.
# (challenge here -- telling python to ignore empty characters / the lack of characters before or after the character match)
# step 4: if they DO match, combine the strings, then add it to another list (LISTB). remove original 2 strings from original list (LISTA)
# step 5: after loop runs, add all remaining strings in LISTA to LISTB..
# step 6: compare all the (now-combined) strings in LISTB. follow same process as above.
# step 7: print final result.

# NOTE: longest common substring problem
# possibly solved by the below code

def longest_common_substring(s1, s2):
   m = [[0] * (1 + len(s2)) for i in range(1 + len(s1))]
   longest, x_longest = 0, 0
   for x in range(1, 1 + len(s1)):
       for y in range(1, 1 + len(s2)):
           if s1[x - 1] == s2[y - 1]:
               m[x][y] = m[x - 1][y - 1] + 1
               if m[x][y] > longest:
                   longest = m[x][y]
                   x_longest = x
           else:
               m[x][y] = 0
   return s1[x_longest - longest: x_longest]

# from there, we need to figure out how to (1) isolate the substring the two strings have in common, (2) find that substring in both strings and use it to add them
# - together, ie: HHHJJF[HSJDDKSFJS] [HSJDDKSFJS]DKJFJK > substring is in a further position in string 1, so add all characters before
# the substring in string 1 to string 2 to get HHHJJFHSJDDKSFJSDKJFJK
