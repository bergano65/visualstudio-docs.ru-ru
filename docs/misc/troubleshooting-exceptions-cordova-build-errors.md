---
title: "Устранение исключений: ошибки сборки Cordova | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# Устранение исключений: ошибки сборки Cordova
В этой статье описываются некоторые из наиболее распространенных сообщений об ошибках, появляющихся при использовании средств Visual Studio для Apache Cordova.  
  
-   [MSBUILD. Ошибка сборки cordova BLD102: отсутствует файл или каталог config.xml](#BLD102)  
  
-   [MSBUILD. Ошибка сборки cordova BLD301: удаленный агент сборки iOS не был настроен](#BLD301)  
  
-   [MSBUILD. Ошибка сборки cordova BLD401: не удалось найти модуль &lt;имя_модуля&gt;](#BLD401)  
  
-   [MSBUILD. Ошибка сборки cordova BLD10205: установите целевой объект Android](#BLD10205)  
  
-   [BLDErr_Build_NodeMissing — не удалось определить путь к исполняемому файлу Node.js.](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 Более общие справочные сведения по устранению ошибок в приложении Cordova см. в разделе [Resolving build error](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/) \(Устранение ошибок сборки\).  
  
##  <a name="BLD102"></a> MSBUILD. Ошибка сборки cordova BLD102: отсутствует файл или каталог config.xml  
 Если отображается эта ошибка, убедитесь, что проект содержит файл config.xml в своем корневом каталоге и что проект находится на локальном компьютере, а не на общем сетевом ресурсе.  
  
 Дополнительные сведения см. в этой [публикации на сайте StackOverflow](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi).  
  
##  <a name="BLD301"></a> MSBUILD. Ошибка сборки cordova BLD301: удаленный агент сборки iOS не был настроен  
 Полный текст ошибки:  
  
-   MSBUILD. Ошибка сборки cordova BLD301: удаленный агент сборки iOS не был настроен. Настройте его в меню "Сервис" \-\>  "Параметры" \-\> "Средства для Apache Cordova" \-\> "Конфигурация удаленного агента". Дополнительные сведения и альтернативные методы см. на странице http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904  
  
 Сведения об установке и настройке удаленного агента сборки для iOS см. в [руководстве по установке iOS.](http://taco.visualstudio.com/en-us/docs/ios-guide/)  
  
##  <a name="BLD401"></a> MSBUILD. Ошибка сборки cordova BLD401: не удалось найти модуль \<имя\_модуля\>  
 Полный текст ошибки:  
  
-   MSBUILD. Ошибка сборки cordova BLD401. Ошибка: BLD00401: не удалось найти модуль \<имя\_модуля\>. Перейдите в меню "Сервис" \-\> "Параметры" \-\> "Средства для Apache Cordova" \-\> "Инструменты Cordova" \-\> "Очистить кэш Cordova" и попробуйте выполнить сборку еще раз.  
  
 Может потребоваться очистка кэша и повторная установка vs\-tac. Дополнительные сведения см. в статье [Повторная установка vs\-tac](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac).  
  
 После очистки кэша удалите папку платформ в проекте. Затем попробуйте выполнить сборку еще раз.  
  
##  <a name="BLD10205"></a> MSBUILD. Ошибка сборки cordova BLD10205: установите целевой объект Android  
 Если отображается эта ошибка, убедитесь, что установлены необходимые зависимости для выбранного целевого устройства с помощью диспетчера пакета SDK для Android \(SDK Manager.exe\).  
  
 Дополнительные сведения о требуемом уровне API и других компонентах пакета SDK для Android см. в статье [Установка зависимостей вручную](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty).  
  
 Также следует проверить папку, используемую в Visual Studio для обнаружения пакета SDK для Android. Сведения об этом см. в статье [Переопределение переменных системной среды](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var).  
  
 Дополнительные сведения об установке правильных компонентов для использования средств см. в статье [Сторонние средства](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose).  
  
##  <a name="BLDErr_Build_NodeMissing"></a> BLDErr\_Build\_NodeMissing — не удалось определить путь к исполняемому файлу Node.js.  
 Если файл Node.js установлен не в расположение по умолчанию, он может быть не найден в Visual Studio. Повторно установите Node.js в расположение по умолчанию. Дополнительные сведения можно найти в [публикации на сайте StackOverflow](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing) и в этой статье о [безопасном обновлении Node.js](http://taco.visualstudio.com/en-us/docs/change-node-version/).  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 Windows 8.1 является обязательной для выбора Windows в качестве целевого объекта в приложении, созданном с помощью инструментов Visual Studio для Apache Cordova.