# problem-in-phyton
Linear Programming Problem: Manufacturing Production Model

Problem Description

A small furniture manufacturing company produces two types of tables: Wooden Tables and Glass Tables. The company wants to maximize its profit. Each type of table requires wood, labor hours, and glass (only for glass tables). The company has limited resources of wood, labor hours, and glass. The goal is to determine how many of each type of table should be produced to maximize profit.

Variables

x1: Number of Wooden Tables to produce

x2: Number of Glass Tables to produce

Objective Function

Maximize Profit:

Profit = 50x1 + 80x2

Where:

Profit from each Wooden Table is $50

Profit from each Glass Table is $80

Constraints

Wood Availability: Each Wooden Table uses 4 units of wood, and each Glass Table uses 2 units of wood. The company has 100 units of wood available.

4x1 + 2x2 ≤ 100

Labor Hours: Each Wooden Table requires 3 hours of labor, and each Glass Table requires 4 hours. The company has 80 hours of labor available.

3x1 + 4x2 ≤ 80

Glass Availability: Each Glass Table uses 2 units of glass, and the company has 30 units of glass available.

2x2 ≤ 30

Non-Negativity Constraints:

x1 ≥ 0, x2 ≥ 0

Source of Information

Assumed data inspired by common manufacturing processes and example LP problems from textbooks.

Optimal Solution

The optimal solution will show how many Wooden Tables and Glass Tables should be produced to maximize profit while satisfying the resource constraints.

from scipy.optimize import linprog

# Coefficients of the objective function (maximize profit)
c = [-50, -80]  # Negative because linprog does minimization by default

# Coefficients of the inequality constraints
A = [[4, 2],   # Wood constraint
     [3, 4],   # Labor constraint
     [0, 2]]   # Glass constraint

# Right-hand side of the inequality constraints
b = [100, 80, 30]

# Bounds for x1 and x2 (non-negativity constraints)
bounds = [(0, None), (0, None)]

# Solving the LP problem
result = linprog(c, A_ub=A, b_ub=b, bounds=bounds, method='highs')

# Output Results
if result.success:
    print("Optimal Solution Found")
    print(f"Number of Wooden Tables: {result.x[0]:.2f}")
    print(f"Number of Glass Tables: {result.x[1]:.2f}")
    print(f"Maximum Profit: ${-result.fun:.2f}")
else:
    print("No Optimal Solution Found")

References

Winston, W. L. (2004). Operations Research: Applications and Algorithms. Duxbury Press.
