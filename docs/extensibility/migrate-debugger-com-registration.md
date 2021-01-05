---
title: Перенесите регистрацию класса COM для отладчика 64-bit | Документация Майкрософт
description: Узнайте, как зарегистрировать классы COM в msvsmon для расширений отладчика без записи в HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 6f28f8eb2935ed2dd8a848ccc3151b9f438fc437
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2021
ms.locfileid: "97862886"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Миграция регистрации класса COM для отладчика 64-bit

Для расширений отладчика, которые регистрируют классы COM в HKEY_CLASSES_ROOT с помощью regasm, regsvr32 или непосредственной записи в реестр и загрузки в *msvsmon.exe* (удаленный отладчик), теперь можно предоставить эту регистрацию для msvsmon без необходимости записи в HKEY_CLASSES_ROOT. Это влияет на устаревшие средства оценки выражений отладчика .NET или модули отладки, настроенные для загрузки в процессе *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>msvsmon-ComClass-DEF

Чтобы использовать этот метод, добавьте **.msvsmon-comclass-def.jsв* файл рядом с msvsmon (installDir:* \Common7\IDE\Remote Debugger\x64 *).

Ниже приведен пример файла msvsmon-ComClass-DEF, который регистрирует один управляемый и один машинный класс:

Имя файла: *MyCompany.MyExample.msvsmon-comclass-def.jsв*

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
