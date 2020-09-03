---
title: Изменение изолированной оболочки с помощью. Файл vsct | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194232"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Изменение изолированной оболочки с помощью файла .Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Проект пользовательского интерфейса для проекта изолированной оболочки Visual Studio содержит файл. vsct, который позволяет указать, какие группы приложений и отдельные команды доступны в приложении. Ниже приведен фрагмент из неизмененного vsct-файла.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 По умолчанию включены большинство команд и групп команд. Чтобы исключить команду или группу команд, просто раскомментируйте эту команду или группу.  
  
 Например, чтобы удалить команды Следующая панель и Предыдущая панель, раскомментируйте `No_PaneNextPaneCommand` записи и `No_PanePrevPaneCommand` .  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Более подробный пример этих настроек см. в разделе [Пошаговое руководство. Создание базового приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Файлы, на которые имеются ссылки  
 Файл Default. vsct для приложения ссылается на следующие файлы. Эти файлы находятся в подкаталоге \Висуалстудиоинтегратион\коммон\инк\ каталога установки пакета SDK для Visual Studio.  
  
|Файл|Описание|  
|----------|-----------------|  
|вбидс. h|Удостоверения пользовательского интерфейса для пакета веб-просмотра.|  
|Аппидкмдусед. vsct|Таблица команд для основных элементов пользовательского интерфейса Visual Studio.|  
|Емулаторкмдусед. vsct|Таблица команд для Emacs и Brief: элементы пользовательского интерфейса эмуляции редактора.|  
|Всдебуггуидс. h|Определяет идентификаторы GUID команд, страницы параметров и других функций отладчика Visual Studio.|  
|Всдбгкмдусед. vsct|Командная таблица для отладчика.|  
  
 Файл Аппидкмдусед. vsct включает элементы пользовательского интерфейса Visual Studio на основе символов, определенных в файле Application. vsct.  
  
 Дополнительные сведения см. в разделе [Конструирование XML-командных таблиц (. Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) и ссылка на [схему XML vsct](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>См. также:  
 [Изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)
