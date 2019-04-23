---
title: Практическое руководство. Изменение пространства имен доменного языка | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 57ec75ec116b3b107b01a139621d3c59ca8ecac9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094915"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Практическое руководство. Изменение пространства имен предметно-ориентированного языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете изменить пространство имен доменного языка. Необходимо внести изменения в **обозреватель DSL**в свойствах проекта Dsl и в сведениях о сборке.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Чтобы изменить пространство имен доменного языка  
  
1. В **обозреватель DSL**, нажмите кнопку **Dsl** узла.  
  
2. В **свойства** измените **пространства имен** свойство.  
  
3. Сохраните решение и преобразования шаблонов.  
  
4. На **проекта** меню, щелкните **Dsl свойства**.  
  
     Отобразятся свойства проекта.  
  
5. Перейдите на вкладку **Приложение** .  
  
6. Изменение **пространство имен по умолчанию** свойство на новое имя пространства имен.  
  
7. Если требуется, чтобы изменить имя сборки, измените **свойство имени сборки.**  
  
8. Если вы изменили имя сборки, откройте DslPackage\Package.tt и обновите следующую строку:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Если вы написали ни строчки кода, не забудьте заменить ссылки на пространство имен и класс в файлах кода.  
  
10. Сброс Visual Studio экспериментального экземпляра.  
  
    1. Удалить **\Users\\**_{имя}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2. В Windows **запустить** меню, выберите **все программы**, **Microsoft Visual Studio 2010 SDK**, **средства**, **сброса Экспериментальный экземпляр**.  
  
11. На **построения** меню, выберите **Перестроить решение**.  
  
## <a name="see-also"></a>См. также  
 [Глоссарий средств предметно-ориентированных языков](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
