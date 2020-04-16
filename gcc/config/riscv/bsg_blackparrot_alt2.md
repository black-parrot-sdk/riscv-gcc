(define_automaton "bsg_blackparrot_alt2")

;; EXE stage functional units, FPU has 3-stage pipeline
(define_cpu_unit "bsg_blackparrot_alt2_alu" "bsg_blackparrot_alt2")
(define_cpu_unit "bsg_blackparrot_alt2_div" "bsg_blackparrot_alt2")

(define_insn_reservation "bsg_blackparrot_alt2_alu" 1
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "unknown,arith,shift,slt,multi,logical,move,nop,auipc,const"))
  "bsg_blackparrot_alt2_alu")

(define_insn_reservation "bsg_blackparrot_alt2_branch" 1
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "branch"))
  "bsg_blackparrot_alt2_alu")

(define_insn_reservation "bsg_blackparrot_alt2_jump" 1
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "jump,call"))
  "bsg_blackparrot_alt2_alu")

(define_insn_reservation "bsg_blackparrot_alt2_load" 3
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "load,fpload"))
  "bsg_blackparrot_alt2_alu")

(define_insn_reservation "bsg_blackparrot_alt2_store" 1
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "store,fpstore"))
  "bsg_blackparrot_alt2_alu")

(define_insn_reservation "bsg_blackparrot_alt2_imul" 4
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "imul"))
  "bsg_blackparrot_alt2_alu")

(define_insn_reservation "bsg_blackparrot_alt2_idiv" 34
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "idiv"))
  "bsg_blackparrot_alt2_div*34")

(define_insn_reservation "bsg_blackparrot_alt2_floats" 5
  (and (eq_attr "tune" "bsg_blackparrot_alt2")
       (eq_attr "type" "fadd,fmul,fdiv,fcvt,fcmp,fmove"))
  "bsg_blackparrot_alt2_alu")
