---
title: Управление внешними инструментами | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a9ebda81f013f42aeac23c9c0a8cc5a0a41f5f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651340"
---
# <a name="managing-external-tools"></a>Управление внешними инструментами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Внешние инструменты можно вызвать прямо из Visual Studio. Несколько инструментов по умолчанию доступны в меню **Сервис**, однако вы можете самостоятельно добавлять другие исполняемые файлы.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Инструменты, доступные в меню «Сервис» Visual Studio
 В меню **Сервис**[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно вызвать следующие инструменты. Их также можно вызывать с по имени из окна **Быстрый запуск**. Например, чтобы вызвать GuidGen.exe, введите **Создать GUID**.

1. Создать GUID: формирует идентификатор GUID.

2. Поиск ошибки: возвращает сообщение об ошибке из введенного значения. Дополнительные сведения см. в разделе [Справочник ERRLOOK](https://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).

3. Инструмент трассировки ATL/MFC: отображает сообщения трассировки отладки в источниках ATL и MFC.

4. PreEmptive Protection — Dotfuscator. Защищает программы платформы .NET от реконструирования.

5. SPY++: отображает процессы, потоки, окна и сообщения окон в графической форме.

6. Редактор конфигураций службы WCF: позволяет создавать и изменять параметры конфигурации для служб WCF.

> [!WARNING]
> Вы можете увидеть другой список внешних инструментов, в зависимости от установленного выпуска Visual Studio и примененных параметров профиля. Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="adding-new-tools"></a>Добавление новых инструментов
 Вы можете добавить внешний инструмент в меню **Сервис**. Откройте диалоговое окно **Внешние инструменты** и нажмите кнопку **Добавить**, а затем введите сведения. Например, следующая запись вызывает открытие проводника Windows в каталоге с файлом, который в настоящий момент открыт в Visual Studio:

1. Заголовок: Открыть расположение файла

2. Команда: explorer.exe

3. Аргументы: /root, "$(ItemDir)"

## <a name="arguments-for-external-tools"></a>Аргументы для внешних средств
 Следующие аргументы являются переменными Visual Studio, которые назначаются при запуске внешнего средства. Ссылки на внешние средства, такие как Spy++ или Блокнот, можно добавить в меню **Сервис** с помощью диалогового окна "Внешние инструменты".

> [!NOTE]
> В строке состояния интегрированной среды разработки отображаются переменные "Текущая строка" и "Текущий столбец" для указания расположения точки вставки в активном редакторе кода. Переменная "Текущий текст" возвращает текст или код, выделенный в этом расположении.

|Имя|Аргумент|Описание|
|----------|--------------|-----------------|
|Путь элемента|$(ItemPath)|Полное имя файла текущего файла (диск + путь + имя файла).|
|Каталог элемента|$(ItemDir)|Каталог текущего файла (диск + путь).|
|Имя файла элемента|$(ItemFilename)|Имя файла текущего файла (имя файла).|
|Расширение элемента|$(ItemExt)|Расширение имени файла текущего файла.|
|Текущая строка|$(CurLine)|Строка текущего положения курсора в окне кода.|
|Текущий столбец|$(CurCol)|Столбец текущего положения курсора в окне кода.|
|Текущий текст|$(CurText)|Выбранный текст.|
|Путь цели|$(TargetPath)|Полное имя файла элемента для сборки (диск + путь + имя файла).|
|Целевой каталог|$(TargetDir)|Каталог элемента для сборки.|
|Имя цели|$(TargetName)|Имя файла элемента для сборки.|
|Расширение цели|$(TargetExt)|Расширение имени файла элемента для сборки.|
|Каталог двоичного файла|$(BinDir)|Конечное расположение двоичного файла, сборка которого выполняется (диск + путь). Например:** \\ . ..\My Documents\Visual Studio \<Version> \\<имя_проекта \> \bin\Debug**|
|Каталог проекта|$(ProjDir)|Каталог текущего проекта (диск + путь).|
|Имя файла проекта|$(ProjFileName)|Имя файла текущего проекта (диск + путь + имя файла).|
|Каталог решения|$(SolutionDir)|Каталог текущего решения (диск + путь).|
|Имя файла решения|$(SolutionFileName)|Имя файла текущего решения (диск + путь + имя файла).|

## <a name="see-also"></a>См. также:
 [Средства сборки С/C++](https://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
