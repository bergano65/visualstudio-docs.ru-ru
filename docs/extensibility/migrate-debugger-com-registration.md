---
title: "Перенос регистрации 64-разрядного отладчика COM класса | Документы Microsoft"
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 19ce2d4cc1ff92240529f35f42845778ded49fdf
ms.lasthandoff: 03/07/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Перенос 64-разрядного отладчика регистрации классов COM

Для расширения отладчика, зарегистрировавшись COM-классов в разделе HKEY_CLASSES_ROOT (с помощью regasm regsvr32, или запись непосредственно в реестр) и загружается msvsmon.exe (удаленный отладчик) стало возможным для предоставления этой регистрации в msvsmon без необходимости записи в раздел HKEY_CLASSES_ROOT. Это влияет на устаревших вычислители выражений отладчика .NET или отладчики, которые настроены для загрузки в процессе msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>Msvsmon comclass четкость

Чтобы использовать этот способ, добавьте файл *.msvsmon comclass-def.json рядом с msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Ниже приведен пример msvsmon comclass-def файла, который регистрирует управляемой и один собственный класс:

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

