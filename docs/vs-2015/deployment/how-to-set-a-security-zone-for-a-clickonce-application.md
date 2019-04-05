---
title: Практическое руководство. Установка зоны безопасности для ClickOnce-приложения | Документация Майкрософт
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
ms.openlocfilehash: a0652f8dbb1acfec111dcc587f3ce4ba2496eb4c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990342"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Практическое руководство. Установка зоны безопасности для ClickOnce-приложения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При установке разрешений управления доступом для кода для приложения ClickOnce необходимо начать с базового набора разрешений на странице **Безопасность** **конструктора проектов**.  
  
 В большинстве случаев вы также можете выбрать зону **Интернет** , содержащую ограниченный набор разрешений, или зону **Локальная интрасеть** , содержащую более обширный набор разрешений. Если приложению требуются настраиваемые разрешения, можно предоставить их, выбрав зону безопасности **Настраиваемая** . Дополнительные сведения о задании настраиваемых разрешений см. в разделе [как: Установка пользовательских разрешений для ClickOnce-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
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
