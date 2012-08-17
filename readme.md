# Dining philosophers problem.

Solution created by using Web Workers and some fancy CSS3 for displaying the state.

## Philosophers

The philosophers are observable state machines (eat-state and think-state). They also have a property indicating their hunger.

### Eat state

While in the eating state philosophers become fed, reducing hunger by 2 each tick. If hunger reaches zero, they drop their forks and starts to think.

### Think state

While in the thinking state philosophers become hungry, increasing hunger by 1 each tick. Each tick they'll try to pick up both forks. If they succeed, they'll start to eat. Otherwise they'll drop any forks they hold and continue to think. This solution prevents resource-hogging, allowing up to two philosophers to eat at the same time.

## Forks

The forks are observables in order to send updates to the main thread, which in turn makes sure other copies of forks in other threads are updated. This is necessary since Web Workers doesn't share objects, it simply copies objects.
