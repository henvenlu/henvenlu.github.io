n = int(input())
state = list(map(int, input().split()))
days = int(input())

seen = {}

while days > 0:
    key = tuple(state)

    if key in seen:
        cycle = seen[key] - days
        days %= cycle
        if days == 0:
            break

    seen[key] = days

    next_state = []

    for i in range(n):
        left = state[i - 1] if i > 0 else 0
        right = state[i + 1] if i < n - 1 else 0
        next_state.append(left ^ right)

    state = next_state
    days -= 1

print(*state)
