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

Aqui estão detalhes sobre cada um dos métodos no `StudentController`:

## `index()`

- `index()`: Recupera todos os estudantes no banco de dados e retorna uma resposta JSON contendo a lista de estudantes.

```sh
public function index(){
    $students= Student::all();
    return response()->json([
        'status'=> 200,
        'students'=>$students,
    ]);
}
```

- `store(Request $request)`: Cria um novo registro de estudante com base nos dados recebidos da solicitação HTTP POST.

```sh
public function store(Request $request)
{
    $student = new Student;
    $student->name= $request->input('name');
    $student->course= $request->input('course');
    $student->email= $request->input('email');
    $student->phone= $request->input('phone');
    $student->save();

    return response()->json([
        'status'=> 200,
        'message'=>'Student Added Successfully',
    ]);
}
```

- `edit($id)`: Recupera um estudante específico com base em seu ID.
```sh
public function edit($id){
    $student= Student::find($id);
    return response()->json([
        'status'=> 200,
        'student'=>$student,
    ]);
}
```

- `update(Request $request, $id)`: Atualiza as informações de um estudante com base no ID fornecido e nos dados recebidos da solicitação HTTP PUT.
```sh
public function update(Request $request, $id){
    $student= Student::find($id);
    $student->name= $request->input('name');
    $student->course= $request->input('course');
    $student->email= $request->input('email');
    $student->phone= $request->input('phone');
    $student->update();
    return response()->json([
        'status'=> 200,
        'message'=>'student modified',
    ]);
}
```

- `destroy($id)`: Exclui um estudante com base em seu ID.
```sh
public function destroy($id){
    $student= Student::find($id);
    $student->delete();

    return response()->json([
        'status'=> 200,
        'message'=>'student Deleted Successfully',
    ]);
}
```


Este controlador faz parte de um projeto Laravel, onde o modelo `Student` é usado para interagir com os dados dos estudantes no banco de dados. Certifique-se de que as rotas apropriadas sejam definidas para cada um desses métodos no arquivo `routes/api.php`.

Certifique-se de configurar corretamente seu ambiente Laravel e banco de dados antes de usar este controlador. Você pode personalizar esse controlador de acordo com as necessidades específicas do seu projeto.


