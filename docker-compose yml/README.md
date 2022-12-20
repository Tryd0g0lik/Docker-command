<table>
  <tr>
    <td colspan='2'>
      <h1>DOCKER COMPOSE</h1>
    </td>
  </tr>
  <tr>
  <td colspan="2">
      <img src="../img_readme/Screenshot_1.png" alt="Название сервиса">
    </td>
  </tr>
  <tr>
  <td colspan="2">
      Название сервиса определяем сами. <br>
      Инструкция уже включает создание образа приложения <code>app</code><br>
      <code>./app</code> указываем место положение приложения. Предварительно создав там Dockerfile.<br>
    </td>
  </tr>
  <tr>
    <th><code>docker-compose stop</code></th>
    <td>Останавливает контейнераы <code>docker-compose stop [options] [SERVICE...]</code> <br>

    </td>
  </tr>
  <tr>
    <th><code>Docker-compose up</code></th>
    <td>Запуск создания контейнера.<br>
      <code>Формат Docker-compose up [options] [SERVICE...]</code> <br>
      <code>Формат Docker-compose up -d</code><br>
      <code>Формат Docker-compose up -d --build</code>
    </td>
  </tr>
  <tr>
    <th><code>Docker-compose down</code></th>
    <td>Останавливает и удаляет контейнеры </td>
  </tr>
  <tr>
    <th><code>Docker logs < id-контейнера ></code></th>
    <td> Смотрим логи контейнера который имеет id < id-контейнера > или иего имя </td>
  </tr>
  <tr>
    <th><code>docker-compose top[SERVICE...]</code></th>
    <td>Проверьте процесс работы в каждом сервисном контейнере</td>
  </tr>
  <tr>
    <th><code>docker-compose pause [SERVICE...]</code></th>
    <td>Служба остановилась Пауза</td>
  </tr>
  <tr>
    <th><code>docker-compose logs[SERVICE...]</code></th>
    <td>Посмотреть журнал</td>
  </tr>
  <tr>
    <td colspan="2"><h2>Флаги</h2>
      <code>-f</code>, --Файл шаблона Compose, указанный файлом файла, Docker по умолчанию-compose.YML может быть указан несколько раз.<br>
      <code>-p</code>, --project-Имя имени указывает имя проекта и использует имя каталога в качестве имени проекта по умолчанию.<br>
      <code>--x-Сеть</code> использует характеристики Docker's Insertable Network -End. <br>
      <code>--x-network-Драйвер</code> драйвера указывает драйвер сетевого бэк -конца, по умолчанию <br>
      --ПРОВОДНЫЙ ВЫХОД БОЛЬШЕ ИНФОРМАЦИИ. <br>
      <code>--build</code> говорим docker-у заново пересоздать образы, каждый раз когда изменили приложение. <br>
      <code>-d</code> запуск создания в background. <br>
      <code>-v</code> - позволяет подключить том.<br>
      <code>--dns=[]</code>           : Установиkивает пользовательские dns-серверы для контейнера <br>
      <code>--network="bridge"</code> : Подключяет контейнер к сети <br>
      … … … <code>'bridge'</code>: Подключите контейнер к мосту через интерфейсы veth <br>
      … … … <code>'none'</code>:Нет сети в контейнере <br>
      … … … <code>'container:< name|id >'</code>:Используйте сетевой стек другого контейнера, указанный через его имя или идентификатор. <br>
      … … … <code>'host'</code>: Используйте сетевой стек хоста внутри контейнера. <br>
      <code>'< network-name >|< network-id >'</code>:подключение к определяемой пользователем сети <br>
      <code>--network-alias=[]</code> : Добавьте псевдоним в сетевой области для контейнера <br>
      <code>--add-host=""</code>      : Добавьте строку в <code>/etc/hosts (host:IP)</code> <br>
      <code>--mac-address=""</code>   : Задает MAC-адрес устройства Ethernet контейнера <br>
      <code>--ip=""</code>     : Задает IPv4-адрес устройства Ethernet контейнера <br>
      <code>--ip6=""</code>           : Задает IPv6-адрес устройства Ethernet контейнера <br>
      <code>--link-local-ip=[]</code> : Установите локальные адреса IPv4/IPv6 для соединения с одним или несколькими устройствами Ethernet контейнера
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <code>Docker-compose [COMMAND] --help</code> <br>
      Или <code>докер-compose help [COMMAND]</code>  Вы можете просмотреть формат конкретной команды.
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <a href="https://docs.docker.com/get-started/08_using_compose/" target="_blank">1. Documetation - Short sintaxis </a> <br>
      <a href="https://docs.docker.com/compose/compose-file/compose-file-v3/#long-syntax-1" target="_blank">2. Documetation - a long sintaxis </a><br>
      <a href="https://docs.docker.com/compose/gettingstarted/" target="_blank">3. Documetation </a><br>
      <a href="https://en.spec-zone.ru/docker~19-compose/" target="_blank">4. Documetation </a><br>
    </td>
  </tr>
</table>

<p>Файл docker-compose должен начинаться с тега версии.
Мы используем "3" так как это - самая свежая версия на момент написания этого кода.</p>

<code> version: "3"</code>

<p>Следует учитывать, что docker-composes работает с сервисами. 1 сервис = 1 контейнер.<br>
Сервисом может быть клиент, сервер, сервер баз данных...<br>
Раздел, в котором будут описаны сервисы, начинается с <code>services</code>.</p>

<code>services</code>
  <p>Будут созданы клиентское и серверное приложения.<br>
  Это означает, что нам нужно два сервиса.<br>
  Первый сервис (контейнер): сервер. Назвать его можно так, как нужно разработчику.<br>
  Понятное название сервиса помогает определить его роль.<br>
  Здесь мы, для именования соответствующего сервиса, используем ключевое слово 'server'.</p>

  <code>server</code>
    <p>Ключевое слово "build" позволяет задать <br>
    путь к файлу Dockerfile, который нужно использовать для создания образа,<br>
    который позволит запустить сервис.<br>
    Здесь 'server/' соответствует пути к папке сервера, <br>
    которая содержит соответствующий Dockerfile.</p>

  <code>build: server/</code>
    <p>Команда, которую нужно запустить после создания образа. <br>
    Следующая команда означает запуск <code>python ./server.py</code>.</p>

  <code>command: python ./server.py</code>
    <p>Вспомните о том, что в качестве порта в <code>server/server.py</code> указан <code> порт 1234</code>.  <br>
    Если нужно обратиться к серверу со своего компьютера (находясь за пределами контейнера),<br>
    следует организовать перенаправление этого порта на порт компьютера.<br>
    Сделать это поможет ключевое слово <code>ports </code>.<br>
    При его использовании применяется следующая конструкция: <code>[порт компьютера]:[порт контейнера]</code><br>
    В данном случае нужно использовать порт компьютера <code>1234</code> и организовать его связь с портом <br>
    <code>1234</code> контейнера (так как именно на этот порт сервер ожидает поступления запросов).</p>

    <pre><code>ports:
      - 1234:1234</code></pre>

  ## Второй сервис (контейнер): клиент.
  <p>Этот сервис назван <code>client</code>.</p>

  <code>client:</code>
    <p>Здесь <code>client/</code> соответствует пути к папке, которая содержит <br>
    файл Dockerfile для клиентской части системы.</p>

  <code>build: client/</code>
    <p>Команда, которую нужно запустить после создания образа.<br>
    Следующая команда означает запуск <code>python ./client.py</code>.</p>

  <code>command: python ./client.py</code>
    <p>Ключевое слово <code>network_mode</code> используется для описания типа сети.
    Тут указывается, что контейнер может обращаться к <code>localhost</code> компьютера.</p>

  <code>network_mode: host</code>
    <p>Ключевое слово <code>pends_on</code> позволяет указывать, должен ли сервис,<br>
    прежде чем запуститься, ждать, когда будут готовы к работе другие сервисы.<br>
    Нужно, чтобы сервис <code>client</code> дождался бы готовности к работе сервиса <code>server</code>.</p>

  <pre><code>depends_on:
    - server</code></pre>
