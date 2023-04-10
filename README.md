<h1 align="center">Projeto Data Em Minutos</h1>


<p align="center">
  <img src="https://github.com/Henriquegcosta/Henriquegcosta/blob/main/images/Image3.jpeg" width="250" title="hover text">
  <img src="https://github.com/Henriquegcosta/Henriquegcosta/blob/main/images/Image2.jpeg" width="250" title="hover text">
  <img src="https://github.com/Henriquegcosta/Henriquegcosta/blob/main/images/Image1.jpeg" width="250" alt="accessibility text">
</p>




Projeto feito em Kotlin, utilizando conhecimentos básicos como (DatePicker) para fazer a seleção da data. Feito junto ao curso de Desenvolvimento Android na Udemy.

Um projeto muito interessante para meu aprendizado, onde consegui utilizar todo o basico de desenvolvimento que consegui aprender durante o curso.

## Codigo do projeto. **(KOTLIN)**

``` 
    private var tvDate : TextView? = null
    private var tvAgeInMinutes : TextView? = null
    private var tvAgeInHours : TextView? = null
    private var tvAgeInSeconds : TextView? = null

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val btnDatePicker : Button = findViewById(R.id.btnPickDate)
        tvDate = findViewById(R.id.tvSelectedDate)
        tvAgeInMinutes = findViewById(R.id.tvAgeInMinutes)
        tvAgeInHours = findViewById(R.id.tvAgeInHour)
        tvAgeInSeconds = findViewById(R.id.tvAgeInSeconds)

        btnDatePicker.setOnClickListener {
            clickDatePicker()

        }
    }

    private fun clickDatePicker(){

        // Acessa o calendario
        val myCalendar = Calendar.getInstance()

        val year = myCalendar.get(Calendar.YEAR)
        val month = myCalendar.get(Calendar.MONTH)
        val day = myCalendar.get(Calendar.DAY_OF_MONTH)
        val dpd =  DatePickerDialog(this, { _, selectedYear, selectedMonth, selectedDayOfMonth ->

            Toast.makeText(this, "Date Picker Work", Toast.LENGTH_SHORT).show()

            //Template para o texto onde mostra a data
            val selectedDate = "$selectedDayOfMonth/${selectedMonth+1}/$selectedYear"

            //Trocando a data assim que selecionar no DatePicker
            tvDate?.text = selectedDate

            val sdf = SimpleDateFormat("dd/MM/yyyy", Locale.ENGLISH)
            val theDate = sdf.parse(selectedDate)

            // So executa o codigo caso a variavel nao esteja vazia
            theDate?.let{
                // Codigo para pegar os minutos desde a data selecionada
                val selectedDateInMinutes = theDate.time / 60000
                val selectedDateInHours = selectedDateInMinutes / 60
                val selectedDateInSeconds = selectedDateInMinutes * 60

                // Nos da o tempo que passou de 1 de janeiro de 1970 as 00:00 ate hoje
                val currentDate = sdf.parse(sdf.format(System.currentTimeMillis()))

                // So executa o codigo caso a variavel nao esteja vazia
                currentDate?.let{
                    val currentDateInMinutes = currentDate.time / 60000
                    val currentDateInHours = currentDateInMinutes / 60
                    val currentDateInSeconds = currentDateInMinutes * 60

                    // Da para a gente quanto tempo passou entre essas datas (Quanto tempo passou da Data selecionada ate a Data Atual)
                    // Diferente da variavel currentDate que apenas pega o tempo que passou de 1 de janeiro de 1970 ate hoje
                    val differenceInMinutes = currentDateInMinutes - selectedDateInMinutes
                    val differenceInHours = currentDateInHours - selectedDateInHours
                    val differenceInSeconds = currentDateInSeconds - selectedDateInSeconds

                    tvAgeInMinutes?.text = differenceInMinutes.toString()
                    tvAgeInHours?.text = differenceInHours.toString()
                    tvAgeInSeconds?.text = differenceInSeconds.toString()
                }

            }



        }, year,month,day)

        dpd.datePicker.maxDate = System.currentTimeMillis() - 86400000
        dpd.show()
```


## Sobre mim

Meu nome é Henrique, tenho 18 anos e estou começando no Desenvolvimento Android. Sempre tive um amor especial por Desenvolvimento Android e agora estou focando em me desenvolver nessa área
Atualmente estou programando apenas em Kotlin. Pretendo aprender Flutter ou Swift futuramente.

Para saber mais sobre minha rotina de uma olhada em meu [Linkedin](https://www.linkedin.com/in/henriquegcosta/) e podemos conversar um pouco mais!.

