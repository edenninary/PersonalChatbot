\documentclass{article}
\usepackage{listings}
\usepackage{color}
\usepackage{hyperref}
\usepackage{geometry}
\geometry{a4paper, margin=1in}

\title{PersonalChatbot}
\author{WhatsApp-based personal chatbot}
\date{}

\begin{document}

\maketitle

\section*{Instructions}

\begin{enumerate}
    \item \textbf{Clone this repository to your machine.}

    \item \textbf{Install the required libraries:}
    \begin{itemize}
        \item Ensure you have all the required libraries and correct versions as listed in the \texttt{requirements.txt} file.
    \end{itemize}

    \item \textbf{Prepare your WhatsApp chat data:}
    \begin{itemize}
        \item Export the desired conversation from WhatsApp and extract the text file.
        \item Name the file \texttt{WhatsappChatOriginal.txt} (without quotes) and place it in the \texttt{PersonalChatbot/src/data\_preprocessing} directory.
    \end{itemize}

    \item \textbf{Configure your model and paths:}
    \begin{itemize}
        \item Fill in the following template with your desired model (if different from the default), the full path to where your data is stored, and the chosen path to save the final model:
    \end{itemize}
    
    \begin{lstlisting}[language=Python, basicstyle=\ttfamily, frame=single]
########################################################
################## Fill This In ########################
base_model_id = "yam-peleg/Hebrew-Mistral-7B"
path_to_data = "full/path/to/PersonalChatbot/src/data_preprocessing/final_outputs/formatted_data.jsonl"
saved_model_path = "path/to/save/model"
########################################################
########################################################
    \end{lstlisting}
    
    \begin{itemize}
        \item Copy and paste this template into the following three files to replace the empty defaults:
        \begin{enumerate}
            \item \texttt{PersonalChatbot/src/chat/chat\_bot.py}
            \item \texttt{PersonalChatbot/src/data\_preprocessing/load\_whatsapp.py}
            \item \texttt{PersonalChatbot/src/training/fine\_tuning\_model.py}
        \end{enumerate}
    \end{itemize}

    \item \textbf{Run the data preprocessing:}
    \begin{itemize}
        \item Change the directory to \texttt{PersonalChatbot/src/data\_preprocessing} and run:
        \begin{lstlisting}[language=bash, basicstyle=\ttfamily, frame=single]
python3 preprocess_start.sh
        \end{lstlisting}
        \item Your processed data should appear in the \texttt{final\_outputs} folder as \texttt{formatted\_data.jsonl}.
    \end{itemize}

    \item \textbf{Fine-tune the model:}
    \begin{itemize}
        \item Change the directory to \texttt{PersonalChatbot/src/training} and run:
        \begin{lstlisting}[language=bash, basicstyle=\ttfamily, frame=single]
python3 fine_tuning_model.py
        \end{lstlisting}
        \item This process may take a while, depending on the amount of data in your WhatsApp chat.
    \end{itemize}

    \item \textbf{Start the chatbot:}
    \begin{itemize}
        \item When step 6 is complete, change the directory to \texttt{PersonalChatbot/src/chat} and run:
        \begin{lstlisting}[language=bash, basicstyle=\ttfamily, frame=single]
python3 chat_bot.py
        \end{lstlisting}
        \item This will create a file named \texttt{conversation.txt} where your conversation with the model will appear. Type your input into the terminal, and the responses will be saved in \texttt{conversation.txt}.
    \end{itemize}
\end{enumerate}

\end{document}
