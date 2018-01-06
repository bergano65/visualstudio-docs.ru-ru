---
title: "Перенос регистрации 64-разрядный отладчик COM класса | Документы Microsoft"
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: "1"
author: gregg-miskelly
ms.author: greggm
manager: ghogen
ms.workload: greggm
ms.openlocfilehash: 737c970555fce8f3cdac118421eddb09f52d7c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Перенос 64-разрядный отладчик регистрации классов COM

Для расширения отладчика, которые регистрации COM-классов в раздел HKEY_CLASSES_ROOT (путем с помощью regasm regsvr32, или непосредственно запись в реестр) и загружается в msvsmon.exe (удаленному отладчику) можно теперь позволяют без этой регистрации для msvsmon для записи в раздел HKEY_CLASSES_ROOT. Это влияет на устаревшие вычислители выражений отладчик .NET или отладчики, которые настроены для загрузки в процесс msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>Msvsmon comclass-def

Чтобы использовать этот способ, добавьте файл *.msvsmon comclass-def.json рядом с msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Ниже приведен пример msvsmon comclass-def файла, который регистрирует один управляемый и один собственный класс.

Имя файла: MyCompany.MyExample.msvsmon-comclass-def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
