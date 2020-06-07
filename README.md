## 2D CFAR Implementation
I used nested loops for RDM and train_cell + guard_cells and for rows and coloum as well.
something like
for RDM:rows
	 for RDM:cols
		for train_cell + guard_cell:rows
			for train_cell + guard_cell:cols

				calculate noise

		using this noise to apply thresholding i.e. calculate the average of the noise across one window, for the sliding window over all the cells.

		if the value of range in doppler map is > threshold = 1
		else = 0

## Values of train and guard band
I did it experimentally choosing the values by running with various sets of values
that it should not be too small that we miss the actual target and it should not be too large that we get all the noise in our range map
the best values I found were
train_cells = 10;
train_band = 8;
guard_cells = 4;
guard_band = 4;

## Sppress the non-thresholded cells at the edges
As after the previous step all the values in RDM would be either 1 or 0 the ones not means those are not thresholded hence suppress them by cheking for the same i.e. if the value not equal to 0 and not equal to 1 = 0