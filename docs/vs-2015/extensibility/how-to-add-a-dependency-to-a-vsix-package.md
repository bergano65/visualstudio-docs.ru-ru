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
ms.openlocfilehash: cbd9426b7a9190872a2b04246d7f051b480a188d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066888"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Практическое руководство. Добавление зависимости в пакет VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить развертывание пакета VSIX, который устанавливает все зависимости, которых еще нет на целевом компьютере. Для этого необходимо включите файл с зависимостями VSIX в файл source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Добавление зависимости  
  
1. Откройте файл source.extension.vsixmanifest в **разработки** представления. Перейдите к **зависимости** вкладку и нажмите кнопку **New**.  
  
2. Чтобы добавить установленное расширение: в **добавить новую зависимость** выберите **установлено расширение** и затем для **имя**, выберите расширение в списке.  
  
3. Чтобы добавить другой файл VSIX, который не установлен:: в **добавить новую зависимость** выберите **файл в файловой системе** , а затем использовать **Обзор** кнопку, чтобы выбрать VSIX.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме 1.0 расширение VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
