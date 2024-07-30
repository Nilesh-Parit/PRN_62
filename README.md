for (int i = 0; i < rwPoint.Count; i++)
                            {
                                var pt = rwPoint[i];
                                if (CheckIfPointLieInPolygon(pt, building.Points))
                                {
                                    RecreationalMargin = 0.0;
                                    lst.Add(new Tuple<int, double, string>(building.BuildingID, RecreationalMargin, ID));
                                    break;
                                }
                                else
                                {
                                    ClsSetback objsetback = new ClsSetback();
                                    objsetback.DetectDistancebetweenPolygon(building.Points, rwPoint, "FrontMargin", out List<Tuple<List<Mathematical_Utility.Point>, string, string, string, string, Mathematical_Utility.Point, List<Mathematical_Utility.Point>>> ListPlotTobuilding1);
 
                                    foreach (var tuple1 in ListPlotTobuilding1)
                                    {
                                        margin = Convert.ToDouble(tuple1.Item3);
                                        RecreationalMargin = margin;
                                    }
 
                                    lst.Add(new Tuple<int, double, string>(building.BuildingID, RecreationalMargin, ID));
                                    break;
                                }
                            }
