library(shiny)
library(babynames)
library(tidyverse)
library(scales)

ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(
      textInput("name", "Name:", value="Ari")
    ),
    mainPanel(
      plotOutput("namePlot")
    )
  )
)

server <- function(input, output) {
  output$namePlot <- renderPlot({
    title = paste0("Number of Babies Born with Name ", input$name)
    babynames %>% 
      filter(name == input$name) %>%
      ggplot() +
      geom_line(aes(year,n, color=sex)) +
      ggtitle(title)
  })
}

# Run the application 
shinyApp(ui = ui, server = server)
