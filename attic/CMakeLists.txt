# The attic is the home for old and unused tools, that are mostly deprecated, but can still be built if needed

if(NOT BUILD_ATTIC)
  # list of binaries/scripts that have been deprecated from the default build. In place, a dummy script will
  # be created for each removed tool that warns the user of its deprecation. It's possible that this list
  # will differ from the below list of subdirectories, so unfortunately it has to be defined separately
  set(DEPRECATED_TOOLS
    check_siemens_dir
    connectgraph
    dmri_tensoreig
    histo_fix_topology
    histo_segment
    label_area
    label_border
    mri_apply_inu_correction
    mri_aseg_edit_reclassify
    mri_aseg_edit_train
    mri_auto_fill
    mri_bc_sc_bias_correct
    mri_build_priors
    mri_cht2p
    mri_classify
    mri_compute_structure_transforms
    mri_convert_mdh
    mri_divide_segmentation
    mri_elastic_energy
    mri_estimate_tissue_parms
    mri_extract_conditions
    mri_fcili
    mri_gcab_train
    mri_gdfglm
    mri_histo_normalize
    mri_ibmc
    mri_interpolate
    mri_label_accuracy
    mri_make_bem_surfaces
    mri_make_density_map
    mri_make_labels
    mri_make_register
    mri_make_template
    mri_mosaic
    mri_ms_EM
    mri_ms_EM_with_atlas
    mri_ms_LDA
    mri_multiscale_segment
    mri_multispectral_segment
    mri_parselabel
    mri_partial_ribbon
    mri_register
    mri_rf_long_label
    mris_add_template
    mris_aseg_distance
    mris_average_parcellation
    mris_classify_thickness
    mris_compute_optimal_kernel
    mris_density
    mri_segment_tumor
    mri_segment_wm_damage
    mris_fbirn_annot
    mris_glm
    mri_simulate_atrophy
    mris_longitudinal_surfaces
    mris_make_map_surfaces
    mris_ms_surface_CNR
    mris_surface_change
    mris_svm_classify
    mris_svm_train
    mris_twoclass
    mris_w_to_curv
    mri_threshold
    mri_apply_autoencoder
    mri_train_autoencoder
    mri_transform_to_COR
    mri_update_gca
    mri_vol2roi
    mri_wmfilter
    mri_xcorr
    oct_rf_train
    oct_train
    rbftest
    regdat2xfm
    repair_siemens_file
    spherical_st
  )
  foreach(TOOL ${DEPRECATED_TOOLS})
    install(CODE "
      message(STATUS \"Configuring attic deprecation notice: ${CMAKE_INSTALL_PREFIX}/bin/${TOOL}\")
      set(TOOL ${TOOL})
      configure_file(${CMAKE_SOURCE_DIR}/attic/notice ${CMAKE_INSTALL_PREFIX}/bin/${TOOL} @ONLY)"
    )
  endforeach()
else()
  # add deprecated subdirectories if we're building the attic
  add_subdirectories(
    check_siemens_dir
    connectgraph
    dmri_tensoreig
    histo_fix_topology
    histo_segment
    label_area
    label_border
    mri_apply_inu_correction
    mri_aseg_edit_reclassify
    mri_aseg_edit_train
    mri_auto_fill
    mri_bc_sc_bias_correct
    mri_build_priors
    mri_cht2p
    mri_classify
    mri_compute_structure_transforms
    mri_convert_mdh
    mri_divide_segmentation
    mri_elastic_energy
    mri_estimate_tissue_parms
    mri_extract_conditions
    mri_fcili
    mri_gcab_train
    mri_gdfglm
    mri_histo_normalize
    mri_ibmc
    mri_interpolate
    mri_label_accuracy
    mri_make_bem_surfaces
    mri_make_density_map
    mri_make_labels
    mri_make_register
    mri_make_template
    mri_mosaic
    mri_ms_EM
    mri_ms_EM_with_atlas
    mri_ms_LDA
    mri_multiscale_segment
    mri_multispectral_segment
    mri_parselabel
    mri_partial_ribbon
    mri_register
    mri_rf_long_label
    mri_segment_tumor
    mri_segment_wm_damage
    mri_simulate_atrophy
    mri_threshold
    mri_train_autoencoder
    mri_transform_to_COR
    mri_update_gca
    mri_vol2roi
    mri_wmfilter
    mri_xcorr
    mris_add_template
    mris_aseg_distance
    mris_average_parcellation
    mris_classify_thickness
    mris_compute_optimal_kernel
    mris_density
    mris_fbirn_annot
    mris_glm
    mris_longitudinal_surfaces
    mris_make_map_surfaces
    mris_ms_surface_CNR
    mris_surface_change
    mris_svm_classify
    mris_svm_train
    mris_twoclass
    mris_w_to_curv
    oct_train
    rbftest
    regdat2xfm
    repair_siemens_file
    spherical_stats
  )
endif()
