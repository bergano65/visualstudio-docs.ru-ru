---
title: "Служебная программа CreateExpInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Экспериментальные построений"
  - "Экспериментальный куст"
  - "экспериментальный экземпляр"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Служебная программа CreateExpInstance
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Используйте служебную программу CreateExpInstance для создания, сброс, или удалить экспериментальный экземпляр Visual Studio. Отладка и тестирование расширения Visual Studio без изменения базовой продукта можно использовать экспериментальный экземпляр.  
  
## Синтаксис  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### Параметры  
 \-Создание  
 Создает в экспериментальном экземпляре.  
  
 \/ Reset  
 Удаляет экспериментальный экземпляр, а затем создает новый.  
  
 \/Clean  
 Удаляет экспериментальный экземпляр.  
  
 \/ VSInstance  
 Имя каталога, содержащего базовый экземпляр Visual Studio для копирования.  
  
 \/ RootSuffix  
 Суффикс для добавления к имени каталога экспериментальный экземпляр.  
  
## Заметки  
 При работе в расширение Visual Studio можно нажать F5, чтобы запустить экспериментальный экземпляр по умолчанию и установить текущего модуля. При наличии не экспериментальный экземпляр Visual Studio создает ту, которая имеет параметры по умолчанию.  
  
 Расположение по умолчанию экспериментальный экземпляр зависит от номера версии Visual Studio. Например, для Visual Studio 2015 расположение является %localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ все файлы в каталоге, считаются частью этого экземпляра. Любые дополнительные экземпляры экспериментальном не удалось загрузить Visual Studio, имя каталога, первоначально в расположении по умолчанию.  
  
 Visual Studio не доступ к реестру системы при открытии экспериментальный экземпляр. Это отличается от предыдущих версий Visual Studio, который используется экспериментальной версии куста реестра.  
  
 Программа CreateExpInstance заменяет служебную программу VsRegEx.  
  
 В следующем примере сбрасывается в экспериментальном экземпляре Visual Studio по умолчанию.  
  
 **\/VSInstance CreateExpInstance.exe\/Reset \= 14.0\/rootsuffix \= Exp**  
  
## См. также  
 [Выпуск продукта](../../misc/releasing-a-visual-studio-integration-product.md)