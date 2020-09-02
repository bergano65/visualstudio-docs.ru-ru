---
title: Настройка IntelliSense для RequireJS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665882"
---
# <a name="customizing-intellisense-for-requirejs"></a>Настройка IntelliSense для RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Начиная с обновления 4 для Visual Studio 2013, поддерживается RequireJS — популярный загрузчик файлов и модулей JavaScript. RequireJS упрощает определение зависимостей между модулями кода и динамическую загрузку модулей по необходимости. При написании кода JavaScript, использующего RequireJS, IntelliSense предлагает модули, на которые вы ссылались из определения модуля или с помощью вызовов `require()` из кода.

 По умолчанию среда Visual Studio предлагает простейшую конфигурацию для RequireJS, поэтому обычно следует настроить собственные параметры конфигурации (то есть определить псевдонимы для библиотек). В этом разделе описываются различные способы настройки Visual Studio для работы с уникальной конфигурацией проекта.

 В этом разделе описываются следующие действия:

- настройка RequireJS в проектах ASP.NET;

- настройка RequireJS в проектах JSProj, которые используются для сборки приложений Apache Cordova, приложений для Магазина Windows и HTML-приложений LightSwitch.

## <a name="customize-requirejs-in-aspnet-projects"></a>настройка RequireJS в проектах ASP.NET;
 Поддержка RequireJS включается автоматически, когда в текущем файле JavaScript встречается ссылка на файл с именем require.js (подробнее см. в подразделе "Определение контекста IntelliSense" раздела [JavaScript IntelliSense](../ide/javascript-intellisense.md)). В проектах ASP.NET ссылки на require.js обычно выполняются с помощью директивы/// \<reference/> в файле _references.js.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Настройка атрибута data-main в проекте ASP.NET
 Для точной имитации работы приложения при запуске редактору JavaScript необходимо знать, какой файл загружается первым при настройке require.js. Обычно это настраивается в HTML-файле приложения с помощью атрибута `data-main` в элементе скрипта, который ссылается на файл require.js, как показано ниже.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 В этом примере скрипт, на который ссылается атрибут data-main (js/app.js), загружается сразу после файла require.js. Файл, который загружается немедленно, является лучшим местом для первой настройки использования RequireJS (с использованием `require.config()` ). Чтобы сообщить редактору JavaScript, какой файл следует использовать `data-main` в приложении, добавьте `data-main` атрибут, а затем измените директиву/// \<reference/> , которая ссылается на require.js в приложении. Например, можно использовать приведенную ниже директиву.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Настройка начальной страницы приложения в проекте ASP.NET
 При запуске приложения RequireJS предполагает, что относительные пути к файлам (например, пути ".. \\ ") задаются относительно HTML-файла, который загрузил библиотеку require.js. В процессе написания кода в редакторе Visual Studio для проекта ASP.NET эта начальная страница неизвестна. Вам необходимо сообщить редактору, какую начальную страницу следует использовать для относительных путей к файлам. Для этого добавьте `start-page` атрибут в директиву/// \<reference/> .

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 Атрибут `start-page` задает URL-адрес страницы, который будет отображаться в браузере при запуске приложения.

## <a name="customize-requirejs-in-jsproj-projects"></a>Настройка RequireJS в проектах JSProj
 Проекты JSProj (файлы которых заканчиваются расширением JSPROJ) используются при сборке приложений для Apache Cordova, приложений для Магазина Windows на основе HTML и HTML-приложений LightSwitch. В отличие от проектов ASP.NET, эти проекты считывают ссылки на JS-файлы из HTML-файлов, имеющихся в проекте. Поэтому при редактировании кода JavaScript в проекте JSProj вы увидите, что поддержка RequireJS включена, если на редактируемый в настоящий момент файл JavaScript есть ссылка в другом HTML-файле, который также ссылается на файл require.js.

 Действия по настройке, которые требуются для проектов ASP.NET, в случае с файлом проекта JSProj не нужны. То есть файлы скриптов, используемые атрибутом `data-main` в теге script, который ссылается на файл require.js, загружаются автоматически для настройки require.js. HTML-файл, ссылающийся на require.js, также используется в качестве начальной страницы приложения.

## <a name="see-also"></a>См. также:
 [IntelliSense для JavaScript](../ide/javascript-intellisense.md)
