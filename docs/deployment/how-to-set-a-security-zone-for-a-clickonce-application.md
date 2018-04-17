---
title: 'Как: Установка зоны безопасности для ClickOnce-приложения | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 1cdc44bd873a891b6478bb9776141695318150b9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Практическое руководство. Установка зоны безопасности для ClickOnce-приложения
При установке разрешений управления доступом для кода для приложения ClickOnce необходимо начать с базового набора разрешений на странице **Безопасность** **конструктора проектов**.  
  
 В большинстве случаев вы также можете выбрать зону **Интернет** , содержащую ограниченный набор разрешений, или зону **Локальная интрасеть** , содержащую более обширный набор разрешений. Если приложению требуются настраиваемые разрешения, можно предоставить их, выбрав зону безопасности **Настраиваемая** . Дополнительные сведения о задании настраиваемых разрешений см. в разделе [Практическое руководство. Установка пользовательских разрешений для ClickOnce-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Задание зоны безопасности  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Перейдите на вкладку **Безопасность** .  
  
3.  Установите флажок **Включить параметры безопасности ClickOnce-приложений** .  
  
4.  Выберите переключатель **Это приложение с частичным доверием** .  
  
     Элементы управления в разделе **Параметры безопасности ClickOnce-приложений** включены.  
  
5.  В раскрывающемся списке **Зона, из которой приложение будет установлено** выберите зону безопасности.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Установка пользовательских разрешений для ClickOnce-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)