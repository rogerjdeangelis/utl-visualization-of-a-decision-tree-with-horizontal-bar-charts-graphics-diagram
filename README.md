# utl-visualization-of-a-decision-tree-with-horizontal-bar-charts-graphics-diagram
Visualization of a decision tree with horizontal bar charts graphics
    %let pgm=utl-visualization-of-a-decision-tree-with-horizontal-bar-charts-graphics-diagram;

    Visualization of a decision tree with horizontal bar charts graphics

    graphic output
    https://tinyurl.com/2twaxkva
    https://github.com/rogerjdeangelis/utl-visualization-of-a-decision-tree-with-horizontal-bar-charts-graphics-diagram/blob/main/ggparty.pdf

    github
    https://tinyurl.com/y2kxnwxf
    https://github.com/rogerjdeangelis/utl-visualization-of-a-decision-tree-with-horizontal-bar-charts-graphics-diagram

    related repo
    https://github.com/rogerjdeangelis/utl_R_and_WPS_decision_trees
    https://github.com/rogerjdeangelis/mySQL-uml-modeling-to-create-entity-diagrams-for-sas-datasets
    https://github.com/rogerjdeangelis/utl-create-simpe-venn-diagram
    https://github.com/rogerjdeangelis/utl-interaction-between-a-Network-Diagram-and-a-Sankey-diagram-r-networkD3
    https://github.com/rogerjdeangelis/utl-R-Diagramming-tool-for-UML-YAML
    https://github.com/rogerjdeangelis/utl-r-reproducitible-example-of-the-fishbone-diagram
    https://github.com/rogerjdeangelis/utl_diagramme_a_flow_with_a_predefined_order_of_the_nodes
    https://github.com/rogerjdeangelis/utl_fishbone_diagram_and_team_solutions_to_a_complex_problem

    StackOverflow
    https://stackoverflow.com/questions/78962795/add-labels-to-terminal-plots-using-the-ggparty-package

    Solution
    https://stackoverflow.com/users/12993861/stefan
    /*               _     _
     _ __  _ __ ___ | |__ | | ___ _ __ ___
    | `_ \| `__/ _ \| `_ \| |/ _ \ `_ ` _ \
    | |_) | | | (_) | |_) | |  __/ | | | | |
    | .__/|_|  \___/|_.__/|_|\___|_| |_| |_|
    |_|
    */

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* CREATE THIS DIAGRAM                                                                                                    */
    /*                                                                                                                        */
    /*                          OUTLOOK                                        Play                                           */
    /*                            /  \                                  +--------+--------+                                   */
    /*                           /    \                        Outlook  |    Yes |     No |                                   */
    /*                          /      \                       ---------+--------+--------+                                   */
    /*                         /        \                        sunny  | 67%  4 |  33% 2 |                                   */
    /*                        /          \                     ---------+--------+--------+                                   */
    /*                       /       outcast rainy              overcast|      0 | 100% 4 |                                   */
    /*                      /              \                   ---------+--------+--------+                                   */
    /*                     /                \                    rainy  | 24%  1 |  75$ 3 |                                   */
    /*                    /                  \                 ---------+--------+--------+                                   */
    /*                 sunny               OUTLOOK                                                                            */
    /*                  /                     /\                                                                              */
    /*                 /                     /  \                                                                             */
    /*                /                     /    \                                                                            */
    /*               /                     /      \                                                                           */
    /*              /                     /        \                                                                          */
    /*             /                     /          \                                                                         */
    /*            /                  overcast      rainy                                                                      */
    /*           /                     /              \                                                                       */
    /*          /                     /                \                                                                      */
    /*    +------------+      +------------+    +------------+                                                                */
    /*    |NN          |      |NNNNNN      |    |NNN         |                                                                */
    /* No |NN 33%      |   No |NNNNNN 100% | No |NNN 75%     |                                                                */
    /*    |NN          |      |NNNNNN      |    |NNN         |                                                                */
    /*    |            |      |            |    |            |                                                                */
    /*    |YYYY        |   Yes|            |    |Y           |                                                                */
    /* Yes|YYYY 67%    |      |            | Yes|Y 25%       |                                                                */
    /*    |YYYY        |      |            |    |Y           |                                                                */
    /*    +------------+      +------------+    +------------+                                                                */
    /*    0 50 100            0 50 100          0 50 100                                                                      */
    /*                                                                                                                        */
    /**************************************************************************************************************************/


    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    options validvarname=v7;
    data sd1.WeatherPlay;
     * we will use labels in R to create factor datatypes
       outlook 1=sunny 2=overcast 3=rainy
       play  1=yes 2=no
     ;
     input   outlook  play ;
    cards4;
    1 0
    1 0
    2 1
    3 1
    3 1
    1 0
    2 1
    1 0
    1 1
    3 1
    1 1
    2 1
    2 1
    3 0
    ;;;;
    run;quit;

    proc freq data=sd1.WeatherPlay;
    tables outlook*play / norow nocol nopercent;
    run;quit;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  WE WILL USE LABELS IN R TO CREATE FACTORS                                                                             */
    /*                                                                                                                        */
    /*  outlook: 1=sunny 2=overcast 3=rainy                                                                                   */
    /*  play:    1=yes   2=no                                                                                                 */
    /*                                                                                                                        */
    /*  SD1.WEATHERPLAY total obs=14   Table of outlook by play                                                               */
    /*                                                                                                                        */
    /*  bs    outlook    play          outlook     play                                                                       */
    /*                                                                                                                        */
    /*   1       1         0           Frequency|       0|       1|                                                           */
    /*   2       1         0           ---------+--------+--------+                                                           */
    /*   3       2         1                  1 |      4 |      2 |                                                           */
    /*   4       3         1           ---------+--------+--------+                                                           */
    /*   5       3         1                  2 |      0 |      4 |                                                           */
    /*   6       1         0           ---------+--------+--------+                                                           */
    /*   7       2         1                  3 |      1 |      3 |                                                           */
    /*   8       1         0           ---------+--------+--------+                                                           */
    /*   9       1         1           Total           5        9                                                             */
    /*  10       3         1                                                                                                  */
    /*  11       1         1                                                                                                  */
    /*  12       2         1                                                                                                  */
    /*  13       2         1                                                                                                  */
    /*  14       3         0                                                                                                  */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*                                               _               _
     _ __  _ __ ___   ___ ___  ___ ___    ___  _   _| |_ _ __  _   _| |_
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|  / _ \| | | | __| `_ \| | | | __|
    | |_) | | | (_) | (_|  __/\__ \__ \ | (_) | |_| | |_| |_) | |_| | |_
    | .__/|_|  \___/ \___\___||___/___/  \___/ \__,_|\__| .__/ \__,_|\__|
    |_|                                                 |_|
    */


    %utlfkil(d:/pdf/ggparty.pdf);

    %utl_rbeginx;
    parmcards4;
    library(ggparty)
    library(haven)
    WeatherPlay<-read_sas("d:/sd1/WeatherPlay.sas7bdat")
    str(WeatherPlay)
    WeatherPlay$play <- factor(as.integer(WeatherPlay$play)
       ,levels = c(0, 1)
       ,labels = c("yes", "no"))
    WeatherPlay$outlook <- factor(as.integer(WeatherPlay$outlook)
      ,levels = c(1,2,3)
      ,labels = c("sunny", "overcast", "rainy"))
    wptree <- ctree(play ~ outlook,
      data = WeatherPlay,
      control = ctree_control(minsplit = 1, minbucket = 1, mincriterion = .01)
    )
    panel_prop <- function(count, PANEL) {
      count / ave(count, PANEL, FUN = sum)
    }
    pdf("d:/pdf/ggparty.pdf", height=10, width=11)
    ggparty(wptree) +
      geom_edge() +
      geom_edge_label() +
      geom_node_splitvar() +
      geom_node_plot(gglist = list(
        aes(
          y = play,
          x = after_stat(panel_prop(count, PANEL)),
          label = after_stat(scales::percent(panel_prop(count, PANEL))),
        ),
        geom_bar(),
        geom_label(stat = "count", hjust = 0),
        coord_cartesian(clip = "off")
      ))
    pdf()
    ;;;;
    %utl_rendx;

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
