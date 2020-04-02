DATA lsbp LIKE LINE OF it_bp_root. 
DATA ls_message LIKE LINE OF ct_validationmessage.
DATA ls_tax_num LIKE LINE OF it_bp_tax_num.
DATA lv_digits TYPE string VALUE '0123456789'.
DATA lv_message TYPE string.
DATA: lv_len_tax TYPE i, lv_tax_digits TYPE string.

LOOP AT it_bp_tax_num INTO ls_tax_num.

*TAX Number validation for Country 'XX'
*where YYY is the tax type 
IF ls_tax_num-bptaxtype = 'YYY' OR ls_tax_num-bptaxtypeforedit = 'YYY'. 
IF ls_tax_num-bptaxnumber(1) <> 'C' AND ls_tax_num-bptaxnumber(1) <> 'I'.
*You need to create the repository of error messages 
CLEAR lv_message. 

SELECT SINGLE FROM yy1messageclassXX FIELDS description
WHERE code = '001' INTO @lv_message.

                    IF sy-subrc = 0.
                        ls_message-msgv1 = lv_message.
                    ELSE.
                        ls_message-msgv1 = 'The Tax Number must start with "C" or "I"'.
                    ENDIF.
      ls_message-msgty = 'E'.
      APPEND ls_message TO ct_validationmessage.
                
ELSE.
                    lv_len_tax = STRLEN( ls_tax_num-bptaxnumber ).
                    IF lv_len_tax <> 12.
                        CLEAR lv_message.
                        SELECT SINGLE FROM yy1_message_class_XX FIELDS description
                            WHERE code = '002' INTO @lv_message.
                            IF sy-subrc = 0.
                               ls_message-msgv1 = lv_message.
                            ELSE.
                              ls_message-msgv1 = 'The length of the Tax Number must be 12. '.
                            ENDIF.
                                    CLEAR lv_message.
                        SELECT SINGLE FROM yy1_message_class_XX FIELDS description
                        WHERE code = '003' INTO @lv_message.
                         IF sy-subrc = 0.
                            ls_message-msgv2 = lv_message.
                       ELSE.
                           ls_message-msgv2 = 'It must start with "C" or "I" + 11 digits'.
                        ENDIF.         
                      ls_message-msgty = 'E'.
                      APPEND ls_message TO ct_validationmessage.
                ELSE.
                    lv_tax_digits = ls_tax_num-bptaxnumber+1.
                    IF NOT lv_tax_digits CA lv_digits.
                        CLEAR lv_message.
                        SELECT SINGLE FROM yy1_message_class_XX FIELDS description
                            WHERE code = '001' INTO @lv_message.
                
                        IF sy-subrc = 0.
                            ls_message-msgv1 = lv_message.
                        ELSE.
                            ls_message-msgv1 = 'The Tax Number must start with "C" or "I" '.
                        ENDIF.
                
                        CLEAR lv_message.
                        SELECT SINGLE FROM yy1_message_class_XX FIELDS description
                            WHERE code = '004' INTO @lv_message.
                
                        IF sy-subrc = 0.
                            ls_message-msgv2 = lv_message.
                        ELSE.
                            ls_message-msgv2 = 'and followed by 11 digits'.
                        ENDIF.
                
                        ls_message-msgty = 'E'.
                
                        APPEND ls_message TO ct_validationmessage.
                    ENDIF.
                ENDIF.
                
ENDIF.          
ENDIF.
ENDLOOP.
