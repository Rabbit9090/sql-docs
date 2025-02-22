---
description: "VisualTotals (MDX)"
title: "VisualTotals (MDX) | Microsoft Docs"
ms.date: 02/17/2022
ms.service: sql
ms.subservice: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
---
# VisualTotals (MDX)


  Returns a set generated by dynamically totaling child members in a specified set, optionally using a pattern for the name of the parent member in the result set.  
  
## Syntax  
  
```  
  
VisualTotals(Set_Expression[,Pattern])  
```  
  
## Arguments  
 *Set_Expression*  
 A valid Multidimensional Expressions (MDX) expression that returns a set.  
  
 *Pattern*  
 A valid string expression for the parent member of the set, that contains an asterisk (*) as the substitution character for the parent name.  
  
## Remarks  
 The specified set expression can specify a set that contains members at any level within a single dimension, generally members with an ancestor-descendant relationship. The **VisualTotals** function totals the values of the child members in the specified set and ignores child members that are not in the set in calculating the result totals. Totals are visually totaled for sets ordered in hierarchy order. If the order of members in sets breaks the hierarchy, results are not visual totals. For example, VisualTotals (USA, WA, CA, Seattle) does not return WA as Seattle, but rather returns the values for WA, CA, and Seattle, then totals these values as the visual total for USA, counting the sales for Seattle twice.  
  
> [!NOTE]  
>  Applying the **VisualTotals** function to dimension members that are not related to a measure or are under the measure group granularity will cause values to be replaced with null.  
  
 *Pattern*, which is optional, specifies the format for the totals label. *Pattern* requires an asterisk (*) as the substitution character for the parent member and the remainder of the text in the string appears in the result concatenated with the parent name. To display a literal asterisk, use two asterisks (\*\*).  
  
## Examples  
 The following example returns the visual total for the third quarter of the 2001 calendar year based on the single descendant specified - the month of July.  
  
```  
SELECT VisualTotals  
   ({[Date].[Calendar].[Calendar Quarter].&[2001]&[3]  
      ,[Date].[Calendar].[Month].&[2001]&[7]}) ON 0  
FROM [Adventure Works]  
```  
  
 The following example returns the [All] member of the Category attribute hierarchy in the Product dimension together with two of its four children. The total returned for the [All] member for the Internet Sales Amount measure is the total for the Accessories and Clothing members only. Also, the pattern argument is used to specify the label for the [All Products] column.  
  
```  
SELECT  
   VisualTotals  
   ({[Product].[Category].[All Products]  
      ,[Product].[Category].[Accessories]  
      ,[Product].[Category].[Clothing]}  
      , '* - Visual Total'  
   ) ON Columns  
, [Measures].[Internet Sales Amount] ON Rows  
FROM [Adventure Works]  
```  
  
## See Also  
 [MDX Function Reference &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
