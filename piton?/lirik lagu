import time
from threading import Thread, Lock
import sys

lock = Lock()

def animate_text(text, delay=0.1):
    with lock:
        for char in text:
            sys.stdout.write(char)
            sys.stdout.flush()
            time.sleep(delay)
        print()

def sing_lyric(lyric, delay, speed):
    time.sleep(delay)
    animate_text(lyric, speed)
          
def sing_song():
    lyrics = [
        ("Baby, whyyy can't you loveee me?", 0.16),
        ("Hold me so close, maybe we can be luuuckyyy", 0.09),
        ("I'm callin' your name", 0.07),
        ("I'm screamin' it outt just lovee... meeee", 0.085),
        ("I know that it's hard for you to lovee..... meeee.....", 0.09),
        ("~ ~ ~", 0.8),
    ]
    delays = [0.3, 6.5, 12.0, 13.1, 17.9, 19.2]
    
    threads = []
    for i in range(len(lyrics)):
        lyric, speed = lyrics[i]
        t = Thread(target=sing_lyric, args=(lyric, delays[i], speed))
        threads.append(t)
        t.start()
    
    for thread in threads:
        thread.join()

if __name__ == "__main__":
    sing_song()
