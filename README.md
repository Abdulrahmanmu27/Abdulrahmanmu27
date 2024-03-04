import pandas as pd
import matplotlib.pyplot as plt

def load_and_prepare_data(targetA_path, targetB_path):
    """
    Load the datasets and prepare them by setting a DateTime index and extracting sequence numbers.
    """
    targetA_df = pd.read_csv(targetA_path, parse_dates=['Time'], index_col='Time')
    targetB_df = pd.read_csv(targetB_path, parse_dates=['Time'], index_col='Time')
    
    targetA_df = extract_sequence_numbers(targetA_df)
    targetB_df = extract_sequence_numbers(targetB_df)
    
    return targetA_df, targetB_df

def extract_sequence_numbers(df):
    """
    Extracts sequence numbers from the 'Info' column.
    """
    df['Sequence_Number'] = df['Info'].str.extract(r'Seq=(\d+)', expand=False).astype(int)
    return df

def plot_sequence_numbers_over_time(df):
    """
    Plots sequence numbers over time.
    """
    plt.figure(figsize=(12, 6))
    plt.plot(df.index, df['Sequence_Number'], marker='o', linestyle='', markersize=2)
    plt.title('Graph 1: Sequence Numbers over Time')
    plt.xlabel('Time')
    plt.ylabel('Sequence Number')
    plt.grid(True)
    plt.show()

def plot_probabilities_of_packet_lengths_improved(df):
    """
    Plots the probabilities of packet lengths with improved readability on the x-axis.
    """
    plt.figure(figsize=(12, 6))
    df['Length'].plot(kind='hist', bins=30, density=True, alpha=0.6)
    plt.gca().yaxis.set_major_formatter(plt.matplotlib.ticker.PercentFormatter(xmax=1))
    plt.title('Graph 2: Probabilities of Packet Lengths (Improved)')
    plt.xlabel('Packet Length')
    plt.ylabel('Probability (%)')
    plt.grid(True)
    plt.tight_layout()
    plt.show()

# Define your file paths
targetA_path = "C:\\Users\\abdul\\Downloads\\targetA.csv"
targetB_path = "C:\\Users\\abdul\\Downloads\\targetB.csv"

# Load and prepare the data
targetA_df, targetB_df = load_and_prepare_data(targetA_path, targetB_path)

# Plotting
plot_sequence_numbers_over_time(targetA_df)
plot_probabilities_of_packet_lengths_improved(targetA_df)
