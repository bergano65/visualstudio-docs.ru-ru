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
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842412"
---
# <a name="createpkgdef-utility"></a>Служебная программа CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Принимает DLL-файл для расширения Visual Studio в качестве параметра и создает pkgdef-файл для библиотеки DLL. Файл pkgdef содержит все данные, которые в противном случае были бы записаны в системный реестр при установке расширения.  
  
> [!NOTE]
> Большинство шаблонов проектов, включенных в пакет SDK для Visual Studio, автоматически создают файлы pkgdef в рамках процесса сборки. Этот документ предназначен для тех, кто хочет создавать пакеты вручную, или преобразовать существующие пакеты для развертывания. pkgdef.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Аргументы  
 /out =`FileName`  
 Обязательный элемент. Задает имя файла выходных данных. pkgdef в `FileName` .  
  
 /codebase  
 Необязательный параметр. Принудительная регистрация с помощью служебной программы CodeBase.  
  
 /Assembly  
 Принудительная регистрация с помощью служебной программы сборки.  
  
 `AssemblyPath`  
 Путь к DLL-файлу, из которого нужно создать pkgdef-файл.  
  
## <a name="remarks"></a>Remarks  
 Развертывание расширения с помощью файлов pkgdef заменяет требования к реестру в более ранних версиях Visual Studio.  
  
 Файлы pkgdef должны быть установлены в одном из следующих расположений:%Локалаппдата%\микрософт\висуал Studio\14.0\Extensions\ или%vsinstalldir%\Common7\IDE\Extensions \\ . Если папка установки —%Локалаппдата%\микрософт\висуал Studio\14.0\Extensions \\ , расширение будет распознано Visual Studio, но по умолчанию будет отключено. Пользователь может включить расширение с помощью **расширений и обновлений**. Если папка установки —%vsinstalldir%\Common7\IDE\Extensions \\ , расширение включено по умолчанию.  
  
> [!NOTE]
> Средство " **расширения и обновления** " нельзя использовать для доступа к расширению, если оно не установлено как часть пакета VSIX.  
  
## <a name="see-also"></a>См. также:  
 [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
