---
title: -Edit (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c4dabbb0c21fd6b4cabb01655485c8158662adb2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422335"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает указанный файл в существующем экземпляре [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Аргументы  
 `file1`  
 Необязательный параметр. Файл, открываемый в существующем экземпляре [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Если экземпляров [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] не существует, создается экземпляр с упрощенным макетом окна, где и открывается `file1`.  
  
 `file2`  
 Необязательный параметр. Один или несколько дополнительных файлов для открытия в существующем экземпляре [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="remarks"></a>Примечания  
 Если файл не указан и существует экземпляр [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], этот экземпляр [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] получает фокус. Если файл не указан и экземпляр [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отсутствует, создается экземпляр [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с упрощенным макетом окна.  
  
 Если существующий экземпляр [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] находится в модальном состоянии, например, если открыто [диалоговое окно "Параметры"](../../ide/reference/options-dialog-box-visual-studio.md), файл открывается в существующем экземпляре, когда [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выходит из модального состояния.  
  
## <a name="example"></a>Пример  
 Этот пример открывает файл `MyFile.cs` в существующем экземпляре [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] либо в новом экземпляре [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], если он еще не существует.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
