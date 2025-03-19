
1. Основной запуск приложения
Класс DemoApplication с аннотацией @SpringBootApplication запускает Spring Boot приложение.
2. Модель пользователя (User)
Класс User описывает сущность пользователя с полями id, lastName, firstName, middleName, birthDate, email, phone.
Аннотации @Entity, @Table(name = "users") говорят о том, что класс связан с таблицей users в БД.
Используется @GeneratedValue(strategy = GenerationType.IDENTITY), что означает автоинкремент id.
3. Репозиторий пользователей (UserRepository)
Интерфейс UserRepository расширяет JpaRepository<User, Long>, что даёт стандартные CRUD-методы без дополнительного кода.
4. Сервис пользователей (UserService)
Обрабатывает бизнес-логику работы с пользователями:
getAllUsers(): получение списка пользователей.
getUserById(Long id): поиск пользователя по id.
saveUser(User user): сохранение пользователя.
deleteUser(Long id): удаление пользователя по id.
5. Контроллер пользователей (UserController)
REST API для управления пользователями:
GET /api/users — получить всех пользователей.
GET /api/users/{id} — получить пользователя по id.
POST /api/users — создать нового пользователя.
DELETE /api/users/{id} — удалить пользователя по id.
6. Безопасность (Basic Auth)
Настроена базовая аутентификация (httpBasic()).
Все API-запросы (/api/**) требуют авторизации.
Используется BCryptPasswordEncoder для хеширования паролей.
csrf().disable() — защита CSRF отключена.
7. Настройки PostgreSQL
Подключение к БД demo на локальном сервере localhost:5432.
Используется Hibernate (JPA) с spring.jpa.hibernate.ddl-auto=update, что автоматически обновляет схему базы.
8.Тесты (JUnit + Mockito) для сервиса и контроллера.
