---
title: Как задать зону безопасности для приложения ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9af4507d7ccd604f82aae675bf87d36c0b039b26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68171414"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Практическое руководство. Установка зоны безопасности для ClickOnce-приложения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При установке разрешений управления доступом для кода для приложения ClickOnce необходимо начать с базового набора разрешений на странице **Безопасность****конструктора проектов**.  
  
 В большинстве случаев вы также можете выбрать зону **Интернет** , содержащую ограниченный набор разрешений, или зону **Локальная интрасеть** , содержащую более обширный набор разрешений. Если приложению требуются настраиваемые разрешения, можно предоставить их, выбрав зону безопасности **Настраиваемая** . Дополнительные сведения о задании настраиваемых разрешений см. в разделе [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Задание зоны безопасности  
  
1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.  
  
2. Перейдите на вкладку **Безопасность** .  
  
3. Установите флажок **Включить параметры безопасности ClickOnce-приложений** .  
  
4. Выберите переключатель **Это приложение с частичным доверием** .  
  
     Элементы управления в разделе **Параметры безопасности ClickOnce-приложений** включены.  
  
5. В раскрывающемся списке **Зона, из которой приложение будет установлено** выберите зону безопасности.  
  
## <a name="see-also"></a>См. также:  
 [Как задать пользовательские разрешения для приложения ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
