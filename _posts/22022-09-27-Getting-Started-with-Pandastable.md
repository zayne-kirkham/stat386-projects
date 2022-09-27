---
layout: post
title:  "Getting Started with Pandastable"
date:   2022-09-27
author: Zayne Kirkham
description: This is a cool project
image: 
---



# Intro


# Full Code

```

# importing packages
import tkinter as tk
import pandas as pd
import pandastable


# setting up some data
df = pd.DataFrame({'one': [1, 2, 3, 4, 5],
                   'two': [2, 4, 6, 8, 10],
                   'three': ["Three", "Six", "Nine", "Twelve", "Fifteen"]})


# Define Tkinter Window
class App(tk.Tk):
    def __init__(self):
        super(App, self).__init__()
        self.geometry("300x200")

        # Initialize tk Frame
        self.frame = tk.Frame(self)
        self.frame.pack()

        # Initialize pandastable
        self.table = self.pt = pandastable.Table(self.frame, dataframe=df, showtoolbar=True, showstatusbar=True)
        self.pt.show()


# Mainloop
if __name__ == '__main__':
    app = App()
    app.mainloop()
```

# See also

