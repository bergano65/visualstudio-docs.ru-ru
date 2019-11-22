---
title: Страницы свойств (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffb1298981481bde063de898dc81c02dad548888
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297824"
---
# <a name="property-pages-javascript"></a>Страницы свойств (JavaScript)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Со **страниц свойств** можно получить доступ к параметрам проекта. Страницы, которые отображаются на **страницах свойств**, можно использовать для изменения свойств проекта.

 Чтобы получить доступ к свойствам проекта, выберите узел проекта в **обозревателе решений**. В меню **Проект** выберите пункт **Свойства**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 На **страницах свойств** отображаются следующие страницы и параметры.

## <a name="configuration-and-platform-page"></a>Страница «Конфигурация и платформа»
 Следующие параметры используются для выбора конфигурации и платформы с целью просмотра или внесения изменений.

 **Configuration** Specifies the configuration settings to display or modify. Доступны следующие параметры: **Отладка** (по умолчанию), **Выпуск**, **Все конфигурации** или определяемая пользователем конфигурация. Дополнительные сведения см. в разделе [Конфигурации отладки и выпуска](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platform** Specifies the platform settings to display or modify. Доступны следующие параметры: **Любой ЦП** (по умолчанию для приложений [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]), **x64**, **ARM**, **x86** или определяемая пользователем платформа. Дополнительные сведения см. в разделе [Конфигурации отладки и выпуска](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Страница «Общие»
 Следующие параметры используются для задания общих свойств проекта.

> [!NOTE]
> Некоторые параметры доступны только в приложениях для Магазина Windows.

 **Output Path** Specifies the location of the output files for the project's configuration. Путь является относительным. Если ввести абсолютный путь, он будет сохранен в проекте. Путь по умолчанию — bin\Debug.

 Если выбраны упрощенные конфигурации сборки, система проекта определяет, следует выполнять построение отладочной или окончательной версии. При выборе пунктов **Отладка**, **Начать отладку** (или нажатии клавиши F5) сборка помещается в расположение отладки независимо от указанного значения параметра **Путь для создаваемых файлов**. Но команда **Построить решение** в меню **Сборка** позволяет разместить сборку в указанном местоположении. Чтобы включить дополнительные конфигурации сборки, в строке меню выберите **Сервис**, **Параметры**. В диалоговом окне **Параметры** разверните узел **Проекты и решения**, выберите **Общие** и снимите флажок **Показывать дополнительные конфигурации построения**. Это позволяет вручную контролировать все значения параметров конфигурации и определять создание отладочной или окончательной версии. For more information, see [NIB: General, Projects and Solutions, Options Dialog Box](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Default Language** Specifies the default language for the project. Язык, выбранный в категории **Часы, язык и регион** панели управления, указывает предпочитаемый язык пользователя. Указанный язык по умолчанию для проекта будет использоваться в случае, если предпочитаемый язык пользователя не соответствует языковым ресурсам, предоставляемым в приложении.

## <a name="debug-page"></a>Страница «Отладка»
 Следующие параметры используются для задания свойств поведения отладки в проекте.

> [!NOTE]
> Некоторые параметры доступны только в приложениях для Магазина Windows.

 **Debugger to Launch** Specifies the default host for the debugger.

- Выберите **Локальный компьютер**, чтобы запустить приложения на главном компьютере Visual Studio. Дополнительные сведения см. в разделе [Запуск приложений на локальном компьютере](https://go.microsoft.com/fwlink/?LinkId=234912).

- Выберите **Симулятор**, чтобы запустить приложение в симуляторе. Дополнительные сведения см. в разделе [Запуск приложений в симуляторе](https://go.microsoft.com/fwlink/?LinkId=234913).

- Выберите **Удаленный компьютер**, чтобы запустить приложение на удаленном компьютере. Дополнительные сведения об удаленной отладке см. в разделе [Запуск приложений на удаленном компьютере](https://go.microsoft.com/fwlink/?LinkId=234914).

  **Launch Application** Specifies whether to start the application when you press F5 or click **Debug**, **Start Debugging**. Выберите **Да** для запуска приложения. В противном случае выберите **Нет**. При выборе варианта **Нет** можно выполнять отладку приложения, если для его запуска использовался другой метод.

  **Debugger Type** Specifies the types of code to debug. Выберите**Только скрипт** для отладки кода JavaScript. Выберите **Только управляемый** для отладки кода, который управляется средой CLR. Выберите **Только машинный** для отладки кода C++. Выберите **Машинный и скрипт** для отладки кода C++ и JavaScript. Выберите **Смешанный (управляемый и машинный)** для отладки управляемого кода и кода C++.

  **Allow Local Network Loopback** Specifies whether access to the IP loopback address is allowed for app testing. Выберите **Да**, чтобы разрешить использование петлевого адреса, если клиентское приложение находится на том же компьютере, где выполняется серверное приложение. В противном случае выберите **Нет**. Это свойство доступно, только если для свойства **Загружаемый отладчик** задано значение **Удаленный компьютер**.

  **Machine Name** Specifies the name of the remote computer to host the debugger. Это свойство доступно, только если для свойства **Загружаемый отладчик** задано значение **Удаленный компьютер**.

  **Require Authentication** Specifies whether the remote computer requires authentication. Это свойство доступно, только если для свойства **Загружаемый отладчик** задано значение **Удаленный компьютер**.
