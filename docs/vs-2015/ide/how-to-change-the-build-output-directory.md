---
title: Практическое руководство. Изменение выходного каталога построения | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cc0f6b30abd8c737db018bbc2bb761afc996d6c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263566"
---
# <a name="how-to-change-the-build-output-directory"></a>Практическое руководство. Изменение выходного каталога построения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете указать расположение выходных данных проекта для каждой конфигурации (для отладки, выпуска или и того и другого).  
  
> [!NOTE]
>  Если у вас есть проект **установки** , см. примечание в конце этой статьи.  
  
## <a name="changing-the-build-output-directory"></a>Изменение выходного каталога сборки  
  
#### <a name="to-change-the-build-output-directory"></a>Порядок изменения выходного каталога сборки  
  
1.  В строке меню выберите **Проект**, *Свойства* **имя_приложения**. Можно также щелкнуть правой кнопкой мыши узел проекта в **обозревателе решений** и выбрать пункт **Свойства**.  
  
2.  Если у вас есть проект Visual Basic, выберите вкладку **Компиляция** . Если у вас есть проект Visual C#, выберите вкладку **Сборка** . Если у вас есть проект C++ или JavaScript, выберите вкладку **Общие** .  
  
3.  В раскрывающемся списке конфигураций в верхней части окна выберите конфигурацию, расположение файла выходных данных которой нужно изменить (отладка, выпуск или все).  
  
     Найдите запись пути вывода (**Выходной путь построения** в Visual Basic, **Выходной каталог** в Visual C++, **Путь вывода** в JavaScript и C#). Укажите новый выходной каталог сборки относительно каталога проекта.  
  
> [!NOTE]
>  В случае с проектом установки изменение значения в поле **Имя выходного файла** приводит к изменению расположения только файла Setup.exe, но не файлов проекта. Дополнительные сведения см. в разделе **Сборка, свойства конфигурации, диалоговое окно "Свойства проекта развертывания"**.  
  
## <a name="see-also"></a>См. также  
 [Страница "Сборка" в конструкторе проектов (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Страница свойств "Общие" (проект)](http://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45)   
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)



