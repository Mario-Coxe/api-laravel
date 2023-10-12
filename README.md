# api-laravel
API BÁSICA usando o Laravel

# COMO FAZER 

comando para criar o projecto:
```sh
composer create-project laravel/laravel example-app
```

comando para criar Controller:
```sh
php artisan make:controller NomeDoController
```

comando para criar Model:
```sh
php artisan make:model NomeDoModel
```

em routes/api.php importe controller que foi criando, por exemplo:

```sh
use App\Http\Controllers\StudentController;
```

depois que coloque as rotas ou os endpoints, exemplo

```sh
Route::get('/students', [StudentController::class, 'index']);
```
referencie sempre o metódo se é (get,post,put ou delete)


# Modelo de Estudante (Student Model)

O código a seguir representa o modelo `Student` em um projeto Laravel. Este modelo é responsável por representar os dados de um estudante no banco de dados. Aqui estão alguns detalhes importantes sobre este modelo:

- `use HasFactory;`: Este modelo utiliza a `HasFactory` do Laravel, que permite a criação de instâncias de estudante de maneira mais conveniente e consistente.

- `protected $table = 'students';`: Este modelo está vinculado à tabela do banco de dados chamada 'students'. Você pode personalizar o nome da tabela, se necessário, alterando essa propriedade.

- `protected $fillable = ['name', 'course', 'email', 'phone'];`: Esta propriedade `$fillable` define os campos que podem ser preenchidos em massa ao criar ou atualizar um registro de estudante. Os campos listados (name, course, email, phone) podem ser preenchidos usando a função `create()` do Eloquent ORM.

Certifique-se de que a tabela 'students' no banco de dados corresponda aos campos definidos neste modelo. Este modelo é usado em conjunto com o controlador `StudentController` para realizar operações CRUD relacionadas a estudantes em seu projeto Laravel.

Personalize este modelo de acordo com as necessidades específicas do seu projeto, como campos adicionais ou regras de validação.




# Controlador do Estudante (StudentController)

Este é um exemplo de um controlador Laravel chamado `StudentController` que gerencia operações relacionadas a estudantes em uma API. Este controlador permite a criação, recuperação, atualização e exclusão de registros de estudantes no banco de dados. Aqui estão algumas das principais funções que este controlador executa:

- `index()`: Recupera todos os estudantes no banco de dados e retorna uma resposta JSON contendo a lista de estudantes.

- `store(Request $request)`: Cria um novo registro de estudante com base nos dados recebidos da solicitação HTTP POST.

- `edit($id)`: Recupera um estudante específico com base em seu ID.

- `update(Request $request, $id)`: Atualiza as informações de um estudante com base no ID fornecido e nos dados recebidos da solicitação HTTP PUT.

- `destroy($id)`: Exclui um estudante com base em seu ID.

Este controlador faz parte de um projeto Laravel, onde o modelo `Student` é usado para interagir com os dados dos estudantes no banco de dados. Certifique-se de que as rotas apropriadas sejam definidas para cada um desses métodos no arquivo `routes/api.php`.

Certifique-se de configurar corretamente seu ambiente Laravel e banco de dados antes de usar este controlador. Você pode personalizar esse controlador de acordo com as necessidades específicas do seu projeto.


