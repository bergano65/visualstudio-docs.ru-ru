---
title: Служебная программа CreatePkgDef | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f450453ce8e336fecb401e30bc777c7b9c8ef7d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990489"
---
# <a name="createpkgdef-utility"></a>Служебная программа CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Принимает DLL-файла для расширения Visual Studio, как параметр и создает файл pkgdef, сопровождающее DLL-файл. Файл pkgdef содержит всю информацию, которая в противном случае должна быть записана в системный реестр при установке расширения.  
  
> [!NOTE]
>  Большая часть шаблонов проектов, которые включены в пакет SDK для Visual Studio автоматически создать файлах pkgdef как часть процесса построения. Этот документ предназначен для тех, кто хочет, чтобы преобразовать существующие пакеты, чтобы использовать развертывание .pkgdef или создание пакетов вручную.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Аргументы  
 /out=`FileName`  
 Обязательный. Задает имя выходного файла .pkgdef для`FileName`.  
  
 /codebase  
 Необязательный параметр. Регистрация принудительно с помощью служебной программы базы кода.  
  
 / Assembly  
 Регистрация принудительно с помощью служебной программы сборки.  
  
 `AssemblyPath`  
 Путь к DLL-файл, из которого требуется создать .pkgdef.  
  
## <a name="remarks"></a>Примечания  
 Развертывание расширения с помощью файлах pkgdef заменяет требования реестра из более ранних версиях Visual Studio.  
  
 Файлах pkgdef должен устанавливаться в одном из следующих расположений: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ или %vsinstalldir%\Common7\IDE\Extensions\\. Если папка установки — %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, расширение будет распознаваться модулем Visual Studio, но будет отключена по умолчанию. Пользователь может включить расширение с помощью **расширения и обновления**. Если папка установки — %vsinstalldir%\Common7\IDE\Extensions\\, расширение включено по умолчанию.  
  
> [!NOTE]
>  **Расширения и обновления** средство не может использоваться для доступа к расширением, если он не установлен как часть пакета VSIX.  
  
## <a name="see-also"></a>См. также  
 [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
