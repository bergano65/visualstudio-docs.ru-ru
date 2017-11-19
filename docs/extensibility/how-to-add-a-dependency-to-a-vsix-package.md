---
title: "Как: Добавление зависимости пакета VSIX | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Как: Добавление зависимости пакета VSIX
Можно настроить развертывание пакета VSIX, который устанавливает все зависимости, которые еще не присутствуют на конечном компьютере. Для выполнения этой задачи включают VSIX зависимости, чтобы файл source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Добавление зависимости  
  
1.  Откройте файл source.extension.vsixmanifest в **разработки** представления. Последовательно выберите пункты **зависимости** и нажмите кнопку **New**.  
  
2.  Чтобы добавить установленное расширение: в **Добавление новых зависимостей** установите флажок **установленное расширение** и затем для **имя**, выбрать расширение в списке.  
  
3.  Чтобы добавить другой файл VSIX, который не установлен:: в **Добавление новых зависимостей** выберите **файл в файловой системе** , а затем используйте **Обзор** кнопку, чтобы выбрать расширение VSIX.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме 1.0 расширение VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)