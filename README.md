# abapGit
DATA lv_check TYPE flag.
DATA lv_count TYPE n.
DATA lt_data TYPE mara_tab.

"DB Fectch
SELECT * FROM mara INTO CORRESPONDING FIELDS OF TABLE lt_data.
IF sy-subrc IS INITIAL.
  lv_check = abap_true.
ENDIF.

"Object
DATA(lo_main) = NEW zsrcl_abapgit_test( ).

IF lo_main IS  BOUND.
  lo_main->get_table_count(
    EXPORTING
      it_data  = lt_data
    IMPORTING
      ev_count = lv_count
  ).
ENDIF.

"outPut
IF lv_check EQ abap_true.
  WRITE / 'Success'.
  WRITE / lv_count.
ELSE.
  WRITE 'Failed'.
ENDIF.

"Bran#1 changes

