---
title: 'Способ: добавить зависимость в пакет VSIX | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4a8f360470b22722a3008ed1ac1c05a411cd47d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800369"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Способ: добавить зависимость в пакет VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить развертывание пакета VSIX, который устанавливает все зависимости, которых еще нет на целевом компьютере. Для этого необходимо включите файл с зависимостями VSIX в файл source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Добавление зависимости  
  
1.  Откройте файл source.extension.vsixmanifest в **разработки** представления. Перейдите к **зависимости** вкладку и нажмите кнопку **New**.  
  
2.  Чтобы добавить установленное расширение: в **добавить новую зависимость** выберите **установлено расширение** и затем для **имя**, выберите расширение в списке.  
  
3.  Чтобы добавить другой файл VSIX, который не установлен:: в **добавить новую зависимость** выберите **файл в файловой системе** , а затем использовать **Обзор** кнопку, чтобы выбрать VSIX.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме 1.0 расширение VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

