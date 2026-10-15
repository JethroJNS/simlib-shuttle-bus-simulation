# Shuttle Bus System Simulation

Simulasi sistem shuttle bus untuk rental mobil dengan rute counterclockwise menggunakan discrete event simulation (DES).

## Sistem

- **3 Lokasi**: Terminal 1, Terminal 2, Car Rental
- **Rute**: LOC3 → LOC1 → LOC2 → LOC3 (counterclockwise)
- **Jarak**: LOC3 → LOC1: 4.5 mil, LOC1 → LOC2: 1.0 mil, LOC2 → LOC3: 4.5 mil

## Parameter

| Parameter | Nilai |
|-----------|-------|
| Kapasitas bus | 20 orang |
| Kecepatan bus | 30 mph |
| Min dwell time | 5 menit |
| Unloading time | U(16, 24) detik |
| Loading time | U(15, 25) detik |

## Random Number Streams

| Stream | Fungsi |
|--------|--------|
| 1 | Interarrival di LOC1 |
| 2 | Interarrival di LOC2 |
| 3 | Interarrival di LOC3 |
| 4 | Unloading times |
| 5 | Loading times |
| 6 | Destination di LOC3 |

## Cara Compile & Run

```bash
gcc -o shuttle_bus.exe shuttle_bus.c simlib.c -lm
./shuttle_bus.exe
cat shuttle_bus.out
```

## Format Input (shuttle_bus.in)

```
14 10 24             # Arrival rates (LOC1, LOC2, LOC3) per hour
20 30                # Bus capacity, speed (mph)
4.5 1.0 4.5          # Distances: LOC3 → LOC1, LOC1 → LOC2, LOC2 → LOC3
0.583 0.417          # Probabilities: destination di LOC3 (→ LOC1, → LOC2)
16 24                # Unloading time range (detik)
15 25                # Loading time range (detik)
5                    # Min dwell time (menit)
80                   # Simulation length (jam)
```

## Output

Program menghasilkan laporan dengan statistik:<br>
(a) Average and maximum number in each queue<br>
(b) Average and maximum delay in each queue<br>
(c) Average and maximum number on the bus<br>
(d) Average, maximum, and minimum time the bus is stopped at each location<br>
(e) Average, maximum, and minimum time for the bus to make a loop (departure from the car rental to the next such departure)<br>
(f) Average, maximum, and minimum time a person is in the system by arrival location