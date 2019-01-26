---
title: Служебная программа CreatePkgDef | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 312bbab46cfb7dec85e42f425b2363c2442e576b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016230"
---
# <a name="createpkgdef-utility"></a>Служебная программа CreatePkgDef
Принимает DLL-файла для расширения Visual Studio, как параметр и создает *.pkgdef* файл сопровождающее *.dll* файл. *.Pkgdef* файл содержит всю информацию, которая в противном случае должна быть записана в системный реестр при установке расширения.  
  
> [!NOTE]
>  Большая часть шаблонов проектов, которые включены в пакет SDK для Visual Studio автоматически создать *.pkgdef* файлы как часть процесса построения. Данный документ предназначен для тех, которые хотят создать пакеты вручную или преобразовать существующие пакеты для использования *.pkgdef* развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>  
```  
  
## <a name="arguments"></a>Аргументы  
 **/ out =&lt;имя файла&gt;**  
 Обязательный. Задает имя *.pkgdef* выходной файл &lt;FileName&gt;.  
  
 **/codebase**  
 Необязательный параметр. Заставляет регистрации с **CodeBase** служебной программы.  
  
 **/ Assembly**  
 Заставляет регистрации с **сборки** служебной программы.  
  
 **&lt;AssemblyPath&gt;**  
 Путь к *.dll* файла, из которого требуется создать *.pkgdef*.  
  
## <a name="remarks"></a>Примечания  
 Развертывание расширения с помощью *.pkgdef* файлов заменяет требования реестра из более ранних версиях Visual Studio.  
  
 *.Pkgdef* файлы должны быть установлены в одном из следующих расположений: 

- *%LocalAppData%\Microsoft\Visual Studio\14.0\Extensions\\* 
 
- *%vsinstalldir%\Common7\IDE\Extensions\\*
    
  Если папка установки *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, расширение будет распознаваться модулем Visual Studio, но будет отключена по умолчанию. Пользователь может включить расширение с помощью **расширения и обновления**. 
   
  Если папка установки *%vsinstalldir%\Common7\IDE\Extensions\\*, расширение включено по умолчанию.  
  
> [!NOTE]
>  **Расширения и обновления** средство не может использоваться для доступа к расширением, если он не установлен как часть пакета VSIX.  
  
## <a name="see-also"></a>См. также  
 [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)