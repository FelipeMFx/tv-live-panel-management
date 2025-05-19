
Built by https://www.blackbox.ai

---

# TV Live Panel

## Project Overview
The TV Live Panel is a web application designed to manage interactive television panels for various prize draws and audience engagement. It showcases real-time data, allows users to interact with several configurations, and presents statistics about participation and draw results.

## Installation
To run this project locally, follow the steps below:

1. **Clone the repository**:
    ```bash
    git clone https://your-repo-url.git
    cd your-repo-directory
    ```
2. **Open the index.html file** with a web browser:
    - Simply open the `index.html` file in your favorite web browser. No server is needed for static files.

## Usage
Upon opening the application, you'll see a navigation menu that allows you to access various sections:
- **Sorteio NF Premiada**: Main draw interface.
- **Prêmio Extra**: Configure and view extra prizes.
- **Palpite Premiado**: Interactive guessing section for games.
- **Audiência**: Displays real-time audience statistics.
- **Fotos / Comentários**: Upload photos and comments related to the event.
- **Sorteio GRV/GRR/Festão**: Manage larger draws.
- **Premiações**: View and manage awards-related information.

Each section contains controls to handle specific interactions and displays relevant data in real time.

## Features
- **TailwindCSS**: Utilizes TailwindCSS for responsive and modern UI styling.
- **Interactive Forms**: Users can interact with forms for submitting entries and managing events.
- **Data Tables**: Real-time display of current draws, numbers, and audience engagement.
- **Gallery Uploads**: Users can upload images and comments associated with events.
- **Charts**: Graphical representation of audience statistics using Chart.js.

## Dependencies
This project relies on the following external libraries:
- **TailwindCSS**: For styling.
- **Font Awesome**: For icons.
- **Chart.js**: For graphical data representation.
- **Google Fonts**: Specifically the 'Inter' font for typography.

You can find these linked directly in the HTML files.

## Project Structure
The project directory contains the following key files:

```
.
├── index.html              # Main page of the application
├── premio-bola-maior.html  # Prize extra management page
├── palpite-premiado.html    # Guessing game interface
├── audiencia.html          # Audience statistics section
├── fotos-comentarios.html   # Photo and comment upload page
├── sorteios.html           # Main draw management page
├── premiacoes.html         # Awards management page
├── editar-imagens.html     # Image editing interface
├── common.css              # Common styles for the application
```

### Additional Notes:
- The project is built using HTML, CSS, and JavaScript ensuring compatibility across web browsers.
- For an improved user experience, ensure that JavaScript is enabled in your browser.

## Contributing
If you'd like to contribute to this project, please create a fork and submit a pull request. We welcome improvements, bug fixes, and new features!

## License
This project is licensed under the MIT License - see the LICENSE file for details.