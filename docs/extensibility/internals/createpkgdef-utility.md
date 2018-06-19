---
title: Программа CreatePkgDef | Документы Microsoft
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
ms.openlocfilehash: b8ae53766a42ac2ed218bc92f59088d27e4434e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135795"
---
# <a name="createpkgdef-utility"></a>Программа CreatePkgDef
DLL-файл для расширение Visual Studio в качестве параметра принимает и создает pkgdef-файл вместе с библиотекой DLL. Pkgdef-файл содержит все сведения, в противном случае будут записаны в системный реестр при установке расширения.  
  
> [!NOTE]
>  Большинство шаблонов проектов, которые включены в пакет SDK для Visual Studio автоматически создавать файлы .pkgdef как часть процесса построения. Данный документ предназначен для тех, кто необходимо вручную создать пакеты, или преобразовать существующие пакеты для использования .pkgdef развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Аргументы  
 / out =`FileName`  
 Обязательно. Задает имя выходного файла .pkgdef для`FileName`.  
  
 /codebase  
 Необязательный. Принудительная регистрация с помощью служебной программы CodeBase.  
  
 / Assembly  
 Принудительная регистрация с помощью служебной программы сборки.  
  
 `AssemblyPath`  
 Путь к DLL-файла, из которого нужно создать .pkgdef.  
  
## <a name="remarks"></a>Примечания  
 Развертывание расширения с помощью файлов .pkgdef заменяет реестром более ранних версиях Visual Studio.  
  
 Файлы .pkgdef должны устанавливаться в одном из следующих расположений: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ или %vsinstalldir%\Common7\IDE\Extensions\\. Если папка установки — %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, модуль будет распознаваемой средой Visual Studio, но будет отключен по умолчанию. Пользователь может включить расширение с помощью **расширения и обновления**. Если папка установки — %vsinstalldir%\Common7\IDE\Extensions\\, расширение включено по умолчанию.  
  
> [!NOTE]
>  **Расширения и обновления** средство не может использоваться для доступа к расширение, если он не установлен в составе пакета VSIX.  
  
## <a name="see-also"></a>См. также  
 [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)