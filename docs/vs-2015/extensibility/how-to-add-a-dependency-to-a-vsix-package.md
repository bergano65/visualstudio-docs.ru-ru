---
title: Как добавить зависимость в пакет VSIX | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697510"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Практическое руководство. Добавление зависимости в пакет VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить развертывание пакета VSIX, устанавливающего все зависимости, которые еще не существуют на целевом компьютере. Для этого включите зависимости VSIX в файл Source. extension. vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Добавление зависимости  
  
1. Откройте файл Source. extension. vsixmanifest в представлении **конструктора** . Перейдите на вкладку **зависимости** и нажмите кнопку **создать**.  
  
2. Чтобы добавить установленное расширение, в диалоговом окне " **Добавление новой зависимости** " выберите **установленное расширение** , а затем в поле **имя**выберите расширение в списке.  
  
3. Чтобы добавить еще не установленный файл VSIX: в диалоговом окне **Добавление новой зависимости** выберите **файл в файловой системе** , а затем нажмите кнопку **Обзор** , чтобы выбрать VSIX.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме расширения VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
