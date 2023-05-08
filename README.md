Download Link: https://assignmentchef.com/product/solved-programming-assignment-6-cs-2223-backtracking-and-the-n-queens-problem
<br>
We crown the semester with the <em>n</em>-Queens Problem.

The challenge is to place <em>n </em>Queens on an <em>n</em>×<em>n </em>board (rectangular array?), so that no two attack each other, i.e. no two Queens may be on the same rank (row), file (column), or diagonal (????).

<ol>

 <li>(24 Points) isLegalPosition(board,<em>n</em>)</li>

</ol>

Write a function isLegalPosition(board,<em>n</em>) that takes a (possibly partial) position and <em>n </em>as arguments and returns TRUE if and only if no two Queens attack each other.

Here is a solution to the 8-Queens Problem:

(1 6 8 3 7 4 2 5)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0Z0ZQZ

Z0ZQZ0Z0

0L0Z0Z0Z

Z0Z0L0Z0

Thus, isLegalPosition((1 6 8 3 7 4 2 5),8) should return TRUE.

1

Because we are implementing a backtracking algorithm, we will restrict ourselves to positions which fill from the top of the board. We will insist then that the first <em>k </em>≤ <em>n </em>positions be filled, i.e. non-zero, but the remaining <em>n </em>− <em>k </em>positions may be zeroes. So the partial solution:

(1 6 8 3 7 0 0 0)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0Z0ZQZ

Z0Z0Z0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

should also have isLegalPosition((1 6 8 3 7 0 0 0),8) return TRUE, while

(1 6 8 3 5 0 0 0)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0ZqZ0Z

Z0Z0Z0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

should cause isLegalPosition((1 6 8 3 5 0 0 0),8) to return FALSE.

Why?

Do you see an elegant way to check that?

<ol start="2">

 <li>(18 Points) NextLegalPosition(board,<em>n</em>)</li>

</ol>

From any (possibly partial) position, we need to be able to find the <em>next </em>legal position. There are, perhaps, three cases here. First, the next legal position from an illegal partial position; second, the next legal position from a <em>legal </em>partial position, and third, the next legal position after a full-fledged solution. We will fill our board from the top down and from left to right, so the next legal position after (illegal) partial position:

(1 6 8 3 5 0 0 0)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0ZqZ0Z

Z0Z0Z0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

is

(1 6 8 3 7 0 0 0)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0Z0ZQZ

Z0Z0Z0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

And the next legal position after (legal!) partial position:

(1 6 8 3 7 0 0 0)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0Z0ZQZ

Z0Z0Z0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

is

(1 6 8 3 7 4 0 0)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0Z0ZQZ

Z0ZQZ0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

Will the next legal position <em>from </em>a legal position <em>always </em>add a Queen to the next rank?

Why? / Why not?

Lastly, the next legal position after our solution:

(1 6 8 3 7 4 2 5)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0L0Z0Z0

0Z0Z0ZQZ

Z0ZQZ0Z0

0L0Z0Z0Z

Z0Z0L0Z0

is

(1 6 8 5 0 0 0 0)

QZ0Z0Z0Z

Z0Z0ZQZ0

0Z0Z0Z0L

Z0Z0L0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

0Z0Z0Z0Z

Z0Z0Z0Z0

(Understanding this is understanding the backtracking–and then the forwarding– we are doing. This is the crux of the method.)

Write a function NextLegalPosition(board,<em>n</em>) that takes a (possibly partial) position and <em>n </em>as arguments and returns a board/position/array that represents the next legal position, or (0<sub>1</sub><em>,</em>0<sub>2</sub><em>,…,</em>0<em><sub>n</sub></em>) if no legal position succeeds “board”.

Hint: It may be useful to write another function Successor(board, <em>n</em>) that returns the next position to “board”, whether legal or not.

<ol start="3">

 <li>(12 Points) Find the “first” solution to the <em>n</em>-Queens Problem for <em>n </em>= 4<em>…</em></li>

</ol>

With isLegalPosition(board,<em>n</em>) and NextLegalPosition(board,<em>n</em>) in your hip pocket, write a program which solves the <em>n</em>-Queens problem for all values between 4 and 100, inclusive.

Your output should give a single solution to each instance of the problem, and it should be the <em>first </em>solution lexicographically.

We saw that the 4-Queens problem has solutions (2, 4, 1, 3) and (3, 1, 4, 2) as its distinct solutions. Your output should be the first of these.

Is our solution to the 8-Queens problem the first one?

<ol start="4">

 <li>(6 Points) Find all solutions to the <em>n</em>-Queens Problem for a particular <em>n</em>.</li>

</ol>

With isLegalPosition(board,<em>n</em>) and NextLegalPosition(board,<em>n</em>) in your hip pocket, write a program which finds all solutions to the <em>n</em>-Queens problem for a single instance of the problem with 4 ≤ <em>n </em>≤ 20, input by the user. Your output should consist of a list of solutions in lexicographical order. And keep a running count/index!

(What constitutes a “solution”?)

For parts 2-4, you can get some gains in efficiency by modifying isLegalPosition(board,<em>n</em>). We will <em>build </em>positions from <em>legal </em>positions. This means that only the last Queen, the last non-zero entry, can cause a position to be illegal. Do you see?

Why are you going to want increased efficiency?

You may find the Wikipedia entry on the “8-Queens puzzle” to be helpful…maybe even interesting.