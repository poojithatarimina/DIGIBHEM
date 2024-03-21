# DIGIBHEM
#python program on music player
import tkinter as tk
from tkinter import filedialog
import pygame

class MusicPlayer:
    def __init__(self, master):
        self.master = master
        self.master.title("MusicPlayer")
        self.master.geometry("300x150")
        
        self.play_button = tk.Button(self.master, text="Play", command=self.play_music)
        self.play_button.pack()

        self.pause_button = tk.Button(self.master, text="Pause", command=self.pause_music)
        self.pause_button.pack()

        self.stop_button = tk.Button(self.master, text="Stop", command=self.stop_music)
        self.stop_button.pack()

        self.open_button = tk.Button(self.master, text="Open", command=self.open_file)
        self.open_button.pack()

        self.music_file = None
        self.paused = False

    def play_music(self):
        if self.music_file:
            if self.paused:
                pygame.mixer.music.unpause()
                self.paused = False
            else:
                pygame.mixer.music.load(self.music_file)
                pygame.mixer.music.play()

    def pause_music(self):
        if pygame.mixer.music.get_busy():
            pygame.mixer.music.pause()
            self.paused = True

    def stop_music(self):
        pygame.mixer.music.stop()

    def open_file(self):
        self.music_file = filedialog.askopenfilename(filetypes=[("MP3 files", "*.mp3")])

def main():
    pygame.init()
    root = tk.Tk()
    app = MusicPlayer(root)
    root.mainloop()

if __name__ == "__main__":
    main()