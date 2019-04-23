---
title: CA2210. Сборки должны иметь допустимые строгие имена | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b286a67b21d022b12f77ffff68a71da88256757
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095780"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210. Сборки должны иметь допустимые строгие имена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не подписана строгим именем, не удалось проверить строгое имя или строгого имени, будет недействителен без текущие параметры реестра компьютера.

## <a name="rule-description"></a>Описание правила
 Это правило получает и проверяет строгое имя сборки. Нарушение возникает, если одно из следующих условий:

- Сборка имеет строгое имя.

- Сборка была изменена после подписания.

- Сборка является отложенной подписью.

- Сборка была подписана неверно или не удалось войти.

- Сборки требуются параметры реестра для проверки. Например чтобы пропустить проверку сборки использовался программы строгих имен (Sn.exe).

  Строгое имя защищает клиентов от случайной загрузки сборки, которая была подменена. Сборки без строгих имен следует развертывать лишь в крайне небольшом числе случаев. При обмене или распространении сборок без правильной подписи сборки могут быть подменены, среда CLR может не загрузить сборку или пользователь может быть вынужден отключить проверку на своем компьютере. Сборку без строгого имени имеет следующие недостатки:

- Не удается проверить их истоков.

- Среда CLR не может предупредить пользователей, если содержимое сборки было изменено.

- Не удалось загрузить в глобальном кэше сборок.

  Обратите внимание на то, что для загрузки и анализа сборки с отложенной подписью, необходимо отключить проверку сборки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 **Чтобы создать файл ключа**

 Используйте один из следующих процедур.

- Используйте средство компоновщик сборок (Al.exe), предоставляемого [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Для [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v1.0 и v1.1, используйте либо <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> или <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> атрибута.

- Для [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], либо использовать `/keyfile` или `/keycontainer` параметр компилятора [/keyfile (определение ключа или пары ключей для подписи сборки)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) или  [ /keycontainer (определение контейнера ключей для подписи сборки)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) параметров компоновщика с ++).

  **Чтобы подписать сборку строгим именем в Visual Studio**

1. В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], откройте решение.

2. В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства.**

3. Нажмите кнопку **подписывание** и выберите **подписать сборку** "флажок".

4. Из **выберите файл ключа строгого имени**выберите **New**.

    **Создание ключа строгого имени** окне будут отображаться.

5. В **имя файла ключа**, введите имя для ключа строгого имени.

6. Выберите, следует ли защитить ключ паролем и нажмите кнопку **ОК**.

7. В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **построения**.

   **Чтобы подписать сборку строгим именем вне Visual Studio**

- Используйте средство строгих имен (Sn.exe), предоставляемый [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Дополнительные сведения см. на странице [Sn.exe (Strong Name Tool)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) (Sn.exe: средство строгих имен).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Только подавить предупреждение из этого правила, если сборка используется в среде, где незаконное содержимое не имеет значения.

## <a name="see-also"></a>См. также
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Практическое руководство. Подписать сборку строгим именем](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (средство строгих имен)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
