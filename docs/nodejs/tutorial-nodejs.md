---
title: "Начало работы с Node.js в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1d91d46b20f82a1700c2d20639b3a8827c92bcb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2018
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Начало работы с Node.js в Visual Studio
В этом учебнике по разработке с помощью Node.js в Visual Studio вы создадите простое веб-приложение Node.js, добавите в него код, изучите некоторые возможности интегрированной среды разработки и запустите приложение. Установите Visual Studio бесплатно [здесь](http://www.visualstudio.com), если еще не сделали это.  

## <a name="create-a-project"></a>Создание проекта
Сначала вы создадите проект веб-приложения Node.js.

1. Откройте Visual Studio 2017.  

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект...**.  

3. В левой области диалогового окна **Новый проект** разверните узел **JavaScript** и выберите **Node.js**. В средней области выберите **Базовое приложение Azure Node.js Express 4** и нажмите кнопку **ОК**.   

     Если шаблон проекта **Базовое приложение Azure Node.js Express 4** отсутствует, щелкните ссылку **Открыть установщик Visual Studio** в левой области диалогового окна **Новый проект**. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Разработка Node.js**, а затем элемент **Изменить**. 

    Visual Studio создаст решение и откроет проект. Файл **app.js** проекта откроется в редакторе (в левой области). Если вы не знакомы с решениями и проектами Visual Studio, см. раздел [Краткое руководство. Создание первого приложения Node.js с помощью Visual Studio](../ide/quickstart-nodejs.md).

4. Если у вас не установлена среда выполнения Node.js, установите его ее с веб-сайта [Node.js](https://nodejs.org/en/download/).

    Как правило, Visual Studio автоматически обнаруживает установленную среду выполнения Node.js. В противном случае вы можете указать в проекте ссылку на установленную среду.

## <a name="add-some-code"></a>Добавление кода

1. В обозревателе решений (правая область) откройте папку представлений, а затем откройте файл index.pug.

1. Замените содержимое следующей разметкой:

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. В папке маршрутов откройте файл index.js.

1. Добавьте следующий код перед вызовом `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Замените вызов функции `router.get` следующим кодом:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

1. После элемента `data` введите `: get`, и IntelliSense покажет функцию getData. Выберите `getData`.

    ![Использование IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Удалите запятую (`,`) перед элементом `"data"`, и выражение будет выделено зеленым цветом (подсветка синтаксиса). Наведите указатель на подсветку синтаксиса.

    ![Просмотр синтаксической ошибки](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    В последней строке этого сообщения указывается, что интерпретатор JavaScript ожидал запятую (`,`).

1. Перейдите на вкладку **Список ошибок**.

    Вы увидите предупреждение и описание, а также имя файла и номер строки.

    ![Просмотр списка ошибок](../nodejs/media/tutorial-nodejs-error-list.png)

1. Исправьте код, добавив запятую (`,`) перед элементом `"data"`.

## <a name="set-a-breakpoint"></a>Задание точки останова

1. В файле index.js щелкните в левом внешнем поле перед следующей строкой кода, чтобы установить точку останова:

    `res.render('index', { title: 'Express', "data": getData() });`

    Точки останова — это один из самых простых и важных компонентов надежной отладки. Точка останова указывает, где Visual Studio следует приостановить выполнение кода, чтобы вы могли проверить значения переменных или поведение памяти либо выполнение ветви кода. 

    ![Задание точки останова](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>Запуск приложения

1. На панели инструментов отладки выберите целевой объект отладки.

    ![Выбор целевого объекта отладки](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. Чтобы запустить приложение, нажмите клавишу **F5** (**Отладка** > **Начать отладку**).

    Отладчик приостановит выполнение в заданной точке останова. Теперь можно изучить состояние приложения.

1. Наведите указатель на функцию `getData`, чтобы увидеть ее свойства в подсказке по данным.

    ![Проверка переменных](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Чтобы продолжить, нажмите клавишу **F5** (**Отладка** > **Продолжить**).

    Приложение откроется в браузере.

    В окне браузера вы увидите заголовок "Express" и фразу "Welcome to Express" в первом абзаце.

1. Нажимайте кнопки, чтобы просмотреть различные изображения.

    ![Выполняемые в браузере приложения](../nodejs/media/tutorial-nodejs-running-in-browser.png)  

1. Откройте интерактивное окно Node.js, последовательно выбрав **Вид** > **Другие окна** > **Интерактивное окно Node.js**.

   ![Открытие интерактивного окна Node.js](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    Интерактивное окно позволяет выполнять любые действия с кодом, включая использование операторов `require()`. В коде на приведенном ниже снимке экрана определяется переменная и отображается расположение интерпретатора Node.js.

   ![Интерактивное окно Node.js](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

1. Закройте веб-браузер.  

## <a name="optional-publish-to-azure-app-service"></a>(Необязательно) Публикация в Службу приложений Azure

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**.

   ![Публикация в службу приложений Azure](../nodejs/media/tutorial-nodejs-publish-to-azure.png)  

1. Выберите цель **Служба приложений Microsoft Azure**.

    В диалоговом окне **Служба приложений** можно войти в учетную запись Azure и подключиться к существующим подпискам Azure.

1. Выполните дальнейшие инструкции, чтобы выбрать подписку, выбрать или создать группу ресурсов, выбрать или создать план службы приложений, а затем, когда будет предложено, выполните инструкции по публикации в Azure. Более подробные инструкции см. на странице [Публикация на веб-сайте Azure с помощью веб-развертывания](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. В окне **Вывод** показан ход выполнения развертывания в Azure.

    После успешного развертывания в браузере откроется приложение, выполняющееся в Службе приложений Azure. Нажмите кнопку, чтобы отобразить изображение.

   ![Приложение, работающее в Службе приложений Azure](../nodejs/media/tutorial-nodejs-running-in-azure.png)  

Поздравляем с завершением этого учебника!

## <a name="next-steps"></a>Следующие шаги 

- Дополнительные сведения об [Инструментах Node.js для Visual Studio](https://github.com/Microsoft/nodejstools/wiki)  
- Дополнительные сведения об [интегрированной среде разработки Visual Studio](../ide/visual-studio-ide.md)  