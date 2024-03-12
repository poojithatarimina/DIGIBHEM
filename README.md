# DIGIBHEM
import pygame
import tkinter as tkr
from tkinter.filedialog import askdirectory
import os

music_player = tkr.Tk()
music_player.title("MUSIC PLAYER USING PYTHON")
music_player.geometry("450x350")

directory = askdirectory()
os.chdir(directory)
song_list = os.listdir()
play_list = tkr.Listbox(music_player,font="times new roman 12 bold",bg='purple',selectmode=tkr.SINGLE)
