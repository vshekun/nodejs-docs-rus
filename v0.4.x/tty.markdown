## TTY

Используйте `require('tty')` чтобы получить доступ к этому модулю.

Пример:

    var tty = require('tty');
    tty.setRawMode(true);
    process.stdin.resume();
    process.stdin.on('keypress', function(char, key) {
      if (key && key.ctrl && key.name == 'c') {
        console.log('graceful exit');
        process.exit()
      }
    });


### tty.open(path, args=[])

Запускает новый процесс с исполняемымы файлом указанным в переменной path в новом псевдо-терминале.

Возвращает массив `[slaveFD, childProcess]`. `slaveFD` это файловый дескриптор конца псевдотерминала, принадлежащего потомку. `childProcess` это объект дочернего процесса.


### tty.isatty(fd)

Возвращает `true` или `false` в зависимости от того принадлежит ли файловый дескриптор `fd` терминалу.


### tty.setRawMode(mode)

Переменная `mode` должна принимать значение `true` или `false`. Это задает режим работы потоков ввода-вывода текущего процесса: raw device или default.


### tty.setWindowSize(fd, row, col)

Вызывает `ioctl()` для установки размеров терминала по файловуму дескриптору `fd`,
ассоциированному с ним.

### tty.getWindowSize(fd)

Возвращает массив `[row, col]` размеров терминала по файловуму дескриптору `fd`,
ассоциированному с ним.

