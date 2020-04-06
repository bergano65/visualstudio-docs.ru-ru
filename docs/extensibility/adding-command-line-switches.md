---
title: Добавление коммутаторов командной строки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740164"
---
# <a name="add-command-line-switches"></a>Добавление коммутаторов командной строки
Вы можете добавить коммутаторы командной строки, которые применяются к вашему VSPackage при выполнении *devenv.exe.* Используйте <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> для объявления названия коммутатора и его свойств. В этом примере коммутатор MySwitch добавляется для подкласса VSPackage под названием **AddCommandSwitchPackage** без каких-либо аргументов и с VSPackage загружается автоматически.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Названные параметры отображаются в следующих описаниях.

||||
|-|-|-|-|
| Параметр | Описание|
| Аргументы | Количество аргументов для коммутатора. Может быть «к», или список аргументов. |
| Нагрузка на спрос | Загрузите VSPackage автоматически, если это установлено до 1, в противном случае установлено до 0. |
| HelpString | Строка справки или идентификатор ресурса строки для отображения с **devenv /?**. |
| name | Выключатель. |
| PackageGuid | Идентификатор GUID пакета. |

 Первое значение Аргументов обычно 0 или 1. Для обозначения того, что весь остаток командной строки является аргументом, может использоваться специальное значение «к» значением. Это может быть полезно для отладки сценариев, в которых пользователь должен пройти строку команды отладчика.

 Значение DemandLoad либо `true` (1) `false` или (0) указывает на то, что VSPackage должен быть загружен автоматически.

 Значение HelpString — это идентификатор ресурса строки, которая отображается в **devenv /?** Справка дисплея. Это значение должно быть в форме "#nnn", где nnn является рядом. Значение строки в файле ресурса должно заканчиваться новым символом строки.

 Значение имени — это название коммутатора.

 Значение PackageGuid — это GUID пакета, который реализует этот коммутатор. IDE использует этот GUID для поиска VSPackage в реестре, к которому применяется коммутатор командной строки.

## <a name="retrieve-command-line-switches"></a>Извлечение переключателей командной строки
 При загрузке пакета можно получить переключатели командной строки, выполнив следующие шаги.

1. В реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> позвоните, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> чтобы получить интерфейс.

2. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> для получения переключателей командной строки, вкоторыестовые пользователем.

   Следующий код показывает, как узнать, был ли вводиться коммутатор командной строки MySwitch пользователем:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Вы несете ответственность за проверку коммутаторов командной строки при загрузке пакета.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Параметры командной строки для Devenv](../ide/reference/devenv-command-line-switches.md)
- [Создание утилиты PkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Файлы Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
