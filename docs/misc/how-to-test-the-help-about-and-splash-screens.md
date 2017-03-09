---
title: "Практическое руководство. Тестирование окна справки о продукте и экранов-заставок | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Диалоговое окно "О программе""
  - "пакеты VSPackage, экраны-заставки"
  - "пакеты VSPackage, фирменная символика"
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Практическое руководство. Тестирование окна справки о продукте и экранов-заставок
После реализации **О программе** поддержка экран\-заставки, и можно тестировать реализация in  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Тестирование Справка о диалоговом окне  
  
1.  От [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в командной строке запустите файл devenv.exe с  **\/setup** switch.  В экспериментальном среде, введите:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Примечание.** Необходимо повторить этот шаг только при изменении  **О программе** данные экрана.  
  
2.  Выполнить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в одном корне реестра, как упомянул ранее, но без  **\/setup** переключатель:  
  
     **devenv \/rootsuffix Exp**  
  
3.  На **Справка** меню выберите команду  **О Microsoft Visual Studio**.  
  
     Имя появляется в VSPackage **Установленные продукты** список.  
  
4.  Выберите в VSPackage из списка.  
  
     Ваша сведения о продукте в VSPackage **Сведения о продукте** текстовое поле.  
  
### Тестирование экран\-заставка  
  
1.  Запустите файл devenv.exe с **\/setup** switch.  В экспериментальном среде, введите:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Примечание.** Необходимо повторить этот шаг только при изменении данных экран\-заставки.  
  
2.  Выполнить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в одном корне реестра, как упомянул выше, но с  **\/splash** переключение вместо  **\/setup** switch.  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     Собственные сведения о продукте и эмблема VSPackage отображаются на экран\-заставку.  
  
## См. также  
 [Фирменная символика в пакетах VSPackage](/visual-cpp/misc/vspackage-branding)