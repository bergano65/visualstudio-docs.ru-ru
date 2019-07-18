---
title: T4 Вывода директива | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9262ec994ec847c38ec8d5c1ad95010a929cc4ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62549533"
---
# <a name="t4-output-directive"></a>Директива Output T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В текстовых шаблонах [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] директива `output` используется для определения расширения файла и кодировки преобразованного файла.  
  
 Например если ваш [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проект содержит файл шаблона с именем **MyTemplate.tt** которого содержит следующую директиву:  
  
 `<#@output extension=".cs"#>`  
  
 затем [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] создаст файл с именем **MyTemplate.cs**  
  
 Директива `output` не требуется в текстовых шаблонах времени выполнения (предварительно обработанных). Вместо этого приложение получает созданную строку, вызывая `TextTransform()`. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Применение директивы output  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 В каждом текстовом шаблоне должна быть только одна директива `output`.  
  
## <a name="extension-attribute"></a>атрибут расширения  
 Указывает расширение файла созданного файла текстового вывода.  
  
 Значение по умолчанию — **.cs**  
  
 Примеры  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Допустимые значения:  
 любое допустимое расширение файла.  
  
## <a name="encoding-attribute"></a>атрибут кодировки  
 Задает кодировку для использования при создании выходного файла. Пример:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Значение по умолчанию — кодировка, используемая файлом текстового шаблона.  
  
 Допустимые значения:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (системное значение по умолчанию)  
  
 Как правило, можно использовать строку WebName или число CodePage любых кодировок, возвращаемых <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
