% Base case: If there is only 1 disk, just move it directly.
move_hanoi(1, StartPeg, EndPeg, _) :-
    write('Move disk from '), write(StartPeg),
    write(' to '), write(EndPeg), nl.

% Recursive case: Move N disks
move_hanoi(N, StartPeg, EndPeg, TempPeg) :-
    N > 1,
    SmallerN is N - 1,

    % Step 1: Move top N-1 disks to TempPeg
    move_hanoi(SmallerN, StartPeg, TempPeg, EndPeg),

    % Step 2: Move the biggest disk to EndPeg
    write('Move disk from '), write(StartPeg),
    write(' to '), write(EndPeg), nl,

    % Step 3: Move the N-1 disks from TempPeg to EndPeg
    move_hanoi(SmallerN, TempPeg, EndPeg, StartPeg).

% Main function the user calls
tower_of_hanoi(N) :-
    move_hanoi(N, 'A', 'C', 'B').
