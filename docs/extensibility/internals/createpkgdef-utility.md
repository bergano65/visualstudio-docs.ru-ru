---
title: Служебная программа CreatePkgDef | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0809c7acde2959fb91aa964fec137f63a7a995dc
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500700"
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
 Обязательно. Задает имя *.pkgdef* выходной файл &lt;FileName&gt;.  
  
 **/codebase**  
 Необязательный. Заставляет регистрации с **CodeBase** служебной программы.  
  
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