# Explanation
After clicking the provided [link](https://jupiter.challenges.picoctf.org/problem/44924/) and
inspecting the html, we get 1/3 of the flag:

`<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->`

Then we inspect the `mycss.css` stylesheet and find:
`/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */`

After that we do the same with `myjs.js`:
`/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?f10be399} */`

# Flag
`picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?f10be399}`
