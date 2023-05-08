Download Link: https://assignmentchef.com/product/solved-rob311-project-2-structured-problem-solving-and-planning
<br>
<h1>Part 1: Inference with Definite Clauses</h1>

Propositional logic can be used to answer questions about <em>entailment</em>, i.e., whether one fact follows logically from another set of facts. If we restrict ourselves to definite clauses, which are Horn clauses with exactly one positive literal, very efficient inference algorithms exist, such as forward-chaining (see AIMA pg. 258). Your task is to:

<ol>

 <li>Implement a simple inference engine to solve problems in propositional logic involving definite clauses only. The engine should accept a knowledge base <em>KB </em>and a query <em>q </em>(which is a propositional symbol) and return <em>true </em>if <em>KB </em>entails <em>q </em>(and false otherwise).</li>

</ol>

You will submit your implementation of inference_method.py through Autolab. Please see the docstring of pl_fc_entails in inference_method.py for a description of the inputs and outputs. The definite clauses will be provided to you in the form of DefiniteClause objects from support.py.

<h1>Part 2: The N-Queens Problem</h1>

The N-queens problem is a classic search and constraint satisfaction problem—the goal is to place <em>N </em>queens on an <em>N </em>×<em>N </em>chessboard such that no queen ‘attacks’ any other. A queen attacks any piece in the same row or column, or that lies along the same diagonal on the board. An example (partial) partial attempt at a solution to the 8-queens problem is shown in Figure 1. We will refer to a queen attacking another queen as a ‘conflict’.

Figure 1: Example partial solution (with a conflict on the main diagonal) to the 8-queens problem (AIMA pg. 72).

Luckily, N-queens is quite easy for local search algorithms to solve, because solutions are distributed fairly densely throughout the state space (see AIMA pg. 221). Your tasks are to:

<ol>

 <li>Implement a greedy initialization algorithm for the N-queens problem, that is, an algorithm which starts with one queen on the board (randomly choose the row for the first column) and adds new queens incrementally until all queens have been placed. The greedy strategy should attempt to minimize the number of conflicts for each new queen that is added. Use the function template in the handout code called py. The function should return a 1× <em>N </em>vector, where the zeroindexed <em>i</em><sup>th </sup>entry is the row number of the queen in the <em>i</em><sup>th </sup>column. The row numbers should also be in the set {0<em>,</em>1<em>,…,N </em>−1} (i.e., zero-indexed). The docstring of initialize_greedy_n_queens provides examples and further details.</li>

 <li>Build a solver that makes use of the Min-Conflicts heuristic (AIMA pg. 221) to place all queens on an <em>N </em>× <em>N </em>board without any conflicts. Note that this will be a <em>randomized </em>algorithm, and hence different runs may produce different results—in certain instances, you may need to run your function two (or more) times to produce a valid solution. Use the function template in the handout code called py, which has extra details in its function’s docstring. You will be graded by a procedure that calls your implementation of initialize_greedy_n_queens to produce an initialization, then uses your min_conflicts_n_queens implementation to search for a conflict-free solution (see the example in the handout code).</li>

</ol>

As with Project #1, you will submit your implementations of initialize_greedy_n_queens.py and min_conflicts_n_queens.py through Autolab. For both the initialization and heuristic search functions, be sure to break any ties (in terms of the minimum conflicts heuristic) randomly – this is key for getting the algorithm to perform well.

<h1>Part 3: Motion Planning for a Dubins Vehicle</h1>

The rapidly-exploring random trees (RRT) algorithms is a widely-used algorithm for sample-based robot path planning, in part because it is able to take into account <em>kinodynamic constraints</em>. These are constraints on velocity and acceleration, for example. RRTs are also able to handle <em>nonholonomic constrains</em>, that is, constraints that involve the possible paths taken (parallel parking is such an example: a car cannot move sideways instantaneously). The algorithm has been discussed in Lecture 9 and a demonstration can be seen in this <a href="https://www.youtube.com/watch?v=xAmN8WnltRY">video </a>after the 1:00 time-stamp.

A popular class of kinodynamic paths is known as Dubins paths. A Dubins path is the shortest curve that connects two points in the two-dimensional Euclidean plane with a constraint on the curvature of the path, and with prescribed initial and final tangents (vectors) to the path. An assumption is made that the vehicle on the path can only travel forward. This is a very useful model for many robotics applications. You can read more about Dubins path <a href="https://en.wikipedia.org/wiki/Dubins_path">here</a>. An example of such a path is shown in Figure 2. Your task is to:

<ol>

 <li>Implement an RRT-based planner for a Dubins-type vehicle in a 2D planar world with circular obstacles. The RRT planning function should accept an RRT problem setup that contains: a map (2D size of the world), a list of circular obstacles, a starting pose, a goal and plenty of helper functions for dubins path generation. The function should produce a list of nodes along a valid paths starting from the start node and reaching the goal state. Use the function template in the handout code called rrt_planning.py. Precise instructions and conditions have been provided in this file. The above mentioned problem-setup as well as a simple test have been implemented in a helper file called rrt_dubins_problem.py, while helpful dubins-type path generation functions have been provided in dubins_path_planning.py. Keep in mind that there are time limits on the tests, which implies it is essential to reach the goal pose fast.</li>

</ol>

<strong>HINT: </strong>A purely random exploration strategy is not fast enough in finding the goal. If you already know the goal pose, a ”smarter” random exploration strategy can be employed for a faster solution.

Figure 2: Example Dubins LRL path.

Note that a major chuck of the problem setup and function implementation has already been provided; for example rrt_dubins_problem.py already contains a propagation and a collision checking function, but you are encouraged to read these implementations to understand the big picture for a successful implementation. The provided code is well documented for your clarification and understanding.