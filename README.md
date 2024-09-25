# Create the figure and axis for a more detailed numerical explanation of the graph
fig, ax = plt.subplots(figsize=(8, 8))

# Define quantities for goods 1 and 2
q1 = np.linspace(0, 10, 100)
q2_budget = (10 - 2 * q1) / 1.5  # Budget line equation: p1*q1 + p2*q2 = Income, with p1=2, p2=1.5, Income=10

# Indifference curve parameters (arbitrary utility function for illustration)
q2_indifference = 8 / (q1 + 1)

# Plot the budget line
ax.plot(q1, q2_budget, label='Budget Line (p1*Δq1 vs. p2*Δq2)', color='blue')

# Plot the indifference curve
ax.plot(q1, q2_indifference, label='Indifference Curve', color='orange')

# Highlight the optimal bundle point (q1 = 2, q2 = 4)
optimal_q1 = 2
optimal_q2 = (10 - 2 * optimal_q1) / 1.5
ax.scatter(optimal_q1, optimal_q2, color='red', zorder=5)
ax.text(optimal_q1 + 0.2, optimal_q2, '(2, 4)\nOptimal Bundle', fontsize=12, color='red', ha='left')

# Illustrate the case where p2*Δq2 > p1*Δq1 with numerical values
# Scenario: Trying to consume 2 more units of good 2
delta_q2 = 2  # Δq2 = 2
additional_cost_q2 = 1.5 * delta_q2  # p2*Δq2 = 1.5 * 2 = 3

# Required reduction in q1 to compensate
delta_q1 = additional_cost_q2 / 2  # Required Δq1 to compensate: p1*Δq1 = 3, so Δq1 = 3/2
new_q1 = optimal_q1 - delta_q1
new_q2 = optimal_q2 + delta_q2

# Plot the new (non-optimal) consumption bundle
ax.scatter(new_q1, new_q2, color='purple', zorder=5)
ax.annotate(f'New Point\n({new_q1:.1f}, {new_q2:.1f})', xy=(new_q1, new_q2), xytext=(new_q1 + 1, new_q2 - 1),
            arrowprops=dict(arrowstyle='->', lw=1.5, color='purple'), fontsize=10, color='purple')

# Highlight the cost discrepancy on the graph
ax.annotate(f'p2*Δq2 = {additional_cost_q2}\np1*Δq1 = {2 * delta_q1}', xy=(4, 7), xytext=(6, 8),
            arrowprops=dict(arrowstyle='->', lw=1.5, color='purple'), fontsize=10, color='purple')

# Labels and formatting
ax.set_xlabel('Quantity of Good 1 (q1)')
ax.set_ylabel('Quantity of Good 2 (q2)')
ax.set_title('Graph Explanation: p2*Δq2 > p1*Δq1 Scenario')
ax.axhline(0, color='black', linewidth=0.5)
ax.axvline(0, color='black', linewidth=0.5)
ax.set_xlim(0, 10)
ax.set_ylim(0, 10)
ax.legend()
ax.grid(True, linestyle='--', linewidth=0.5)

# Show the plot
plt.show()

