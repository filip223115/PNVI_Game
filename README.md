# PNVI_Game
Имплементација на 3D игра во Godot 

1. Вовед 

Во оваа игра, играчот се движи низ 3D парк во потрага по скриени богатства. Играта е дизајнирана во платформата Godot и вклучува различни механики, како движење на играчот, собирање предмети, и одбројување на време. Целта на играчот е да собере сите скриени богатства пред да истече времето. 

 

2. Карактеристики на играта 

Играта има следниве главни карактеристики: 

Движење на играчот: Играчот може да се движи низ паркот со помош на тастатурата. Со користење на копчињата „W“ (напред), „S“ (назад), „A“ (лево) и „D“ (десно) играчот се движи низ околината. 

Собирање на богатства: Во паркот се распоредени богатства. Кога играчот ќе дојде во контакт со овие предмети, резултатот на играчот се зголемува. 

Околина на паркот: Паркот е изграден од дрвја, клупи, фонтани и други природни објекти. 

Тајмер: Одбројувачот започнува кога играта започнува и ја предизвикува динамиката на играта. Играта завршува кога времето истекува и на екран се покажува “Game Over” 


3. Техничка имплементација 

Движење на играчот: 

За движење на играчот користевме скрипта која ја следи позицијата на играчот и го менува неговото преместување врз основа на влезните сигнали од тастатурата. 

if Input.is_action_just_pressed("jump") and is_on_floor(): velocity.y = JUMP_VELOCITY 

# Get the input direction and handle the movement/deceleration. 
# As good practice, you should replace UI actions with custom gameplay actions. 
var input_dir := Input.get_vector("left", "right", "forward", "backward") 
var direction := (transform.basis * Vector3(input_dir.x, 0, input_dir.y)).normalized() 
if direction: 
    velocity.x = direction.x * SPEED 
    velocity.z = direction.z * SPEED 
else: 
    velocity.x = move_toward(velocity.x, 0, SPEED) 
    velocity.z = move_toward(velocity.z, 0, SPEED) 
 
 

Оваа скрипта овозможува играчот да се движи во 3D просторот користејќи ги копчињата за насоки. 

Собирање на богатства: 

Богатствата се претставени како 3D објекти. Кога играчот ќе дојде во контакт со предмет, тој исчезнува и се додава на резултатот. 

 

Околина на паркот: 

Паркот беше изграден со користење на различни 3D модели за дрвја, клупи, цветови, фонтана и друго.  

Тајмер: 

Одбројувачот е имплементиран со користење на timer  

func _on_timer_timeout() -> void:  

total_time -= 1  

label.text=str(total_time) 

if total_time < 0: 
    gameOver.text = "GAME OVER" 
 
