---
title: Практическое руководство. Добавление зависимости в пакет VSIX | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697510"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Практическое руководство. Добавление зависимости в пакет VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить развертывание пакета VSIX, который устанавливает все зависимости, которых еще нет на целевом компьютере. Для этого необходимо включите файл с зависимостями VSIX в файл source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Добавление зависимости  
  
1. Откройте файл source.extension.vsixmanifest в **разработки** представления. Перейдите к **зависимости** вкладку и нажмите кнопку **New**.  
  
2. Чтобы добавить установленное расширение: в **добавить новую зависимость** выберите **установлено расширение** и затем для **имя**, выберите расширение в списке.  
  
3. Чтобы добавить другой файл VSIX, который не установлен:: в **добавить новую зависимость** выберите **файл в файловой системе** , а затем использовать **Обзор** кнопку, чтобы выбрать VSIX.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме 1.0 расширение VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
