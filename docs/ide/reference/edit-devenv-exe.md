---
title: -Edit (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47db943d60abc23447aa579e85377a00cf551cae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Открывает указанный файл в существующем экземпляре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Аргументы  
 `file1`  
 Необязательный. Файл, открываемый в существующем экземпляре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Если экземпляров [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не существует, создается экземпляр с упрощенным макетом окна, где и открывается `file1`.  
  
 `file2`  
 Необязательный. Один или несколько дополнительных файлов для открытия в существующем экземпляре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="remarks"></a>Примечания  
 Если файл не указан и существует экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], этот экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] получает фокус. Если файл не указан и экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отсутствует, создается экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с упрощенным макетом окна.  
  
 Если существующий экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] находится в модальном состоянии, например, если открыто [диалоговое окно "Параметры"](../../ide/reference/options-dialog-box-visual-studio.md), файл открывается в существующем экземпляре, когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] выходит из модального состояния.  
  
## <a name="example"></a>Пример  
 Этот пример открывает файл `MyFile.cs` в существующем экземпляре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] либо в новом экземпляре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], если он еще не существует.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)